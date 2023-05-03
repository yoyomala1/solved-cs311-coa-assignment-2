Download Link: https://assignmentchef.com/product/solved-cs311-coa-assignment-2
<br>
<span class="kksr-muted">Rate this product</span>

<table>

 <tbody>

  <tr>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

   <td></td>

  </tr>

  <tr>

   <td colspan="2" rowspan="1"></td>

   <td></td>

  </tr>

 </tbody>

</table>

Write an assembler for the ToyRISC ISA.

Input to the Program

1. full path to the assembly program.2. full path to the object file to be created.

Output of the Program

• the program must create the object file at the specified location. Broad Outline of the Steps

The mechanism of assembly has already been discussed in class. As an example, consider the assembly of this instruction from assignment 1’s statement: load %x0, $a, %x4 in Table 1.

Table 1: Assembly of load %x0, $a, %x4

The task of assembly has been further simplified. We have done the parsing of the assembly program for you (git clone https://gitea.iitdh.ac.in: 443/rajshekar.k/CS311_assignment2.git).

<ul>

 <li>For all labels, both in data and in code, we have set up the symbol table that maps label to address. To get the address corresponding to a label str, simply call ParsedProgram.symtab.get(str).</li>

 <li>Similarly, instructions are also gathered in a simple array. To access the in-struction at a given address addr, simply call ParsedProgram.getInstructionAt(addr).1</li>

</ul>

Field

Value

Binary Representation

Operation

rs1 rd imm

load

x0 x4 0

10110000000010000000000000000000 (recall that ‘a’ refers to address 0)

Full Instruction

10110000000010000000000000000000 = -1341652992 (signed representation)

<ul>

 <li>Each instruction is represented by an object of the Instruction class (see generic/Instruction). You can get the operation type and the operands by calling the appropriate functions mentioned in this class.</li>

 <li>EachoperandisrepresentedbyanobjectoftheOperandclass(seegeneric/Operand). You can get (i) the operand type – that is, is it a register operand, an im-mediate, or a label, and (ii) the value – that is, the register number, theimmediate value, or the label string.You only need to complete the function src.generic.Simulator.simulate(). The expected format of the object file is as follows:</li>

</ul>

<ul>

 <li>Header: Here, you simply write the address of the first instruction. This is an integer, and therefore 4 bytes long.</li>

 <li>Data: Here, you write all the static data one after another. Each datum is 4 bytes long.</li>

 <li>Text: Here, you write the encoded instructions one after another. Each instruction is 4 bytes long.Please see the following example: . dataa10b20. textload %x0, $a, %x4 endThe given assembly file will contain the integers (and not strings!) 2, 10, 20, −1341652992, −402653184. The header consists of the instruction of the first instruction, in this case 2. The two data follow. The binary equivalents of the load and end instructions are then placed.You may read the file that you create using the xxd command. Running, Submitting and Testing</li>

</ul>

<ul>

 <li>To run your program, the arguments are &lt;path-to-assembly-program&gt; &lt;path-to-object-file&gt;. There are two way of running: (i) through Eclipse, (ii) by exporting a jar file. Run the command ant in the folder which contains src and build.xml. It will compile your code. If there are no errors, run the command ant make-jar. A jar file is created at the location jars/assembler.jar. Now to run your program, run this command on the terminal: java -Xmx1g -jar &lt;path-to-jar-file&gt; &lt;path-to-assembly-program&gt; &lt;path-to-object-file&gt;.</li>

 <li>You may test against the programs you submitted in your previous as- signment.2</li>

</ul>

• You are expected to submit a zip archive of the src folder. The name ofyour zip archive should be “&lt;entry-number-1&gt; &lt;entry-number-2&gt; assignment2.zip”.

• Test if your submission is in the correct format. Run the script pythontest zip.py &lt;path-to-zip-file&gt; in the same folder that contains build.xml, test cases, and test zip.py. As in the previous assignment, the scriptwill test against some test cases.