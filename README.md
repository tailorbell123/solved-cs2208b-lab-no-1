Download Link: https://assignmentchef.com/product/solved-cs2208b-lab-no-1
<br>
COMPUTER INSTRUCTION SET ARCHITECTURE

An <em>instruction set architecture</em>, or ISA, is an abstract model of a computer that describes <em>what </em>it does, rather than <em>how </em>it does it. You could say that a computer’s instruction set architecture is its <em>functional definition</em>. Essentially, the ISA is concerned with a computer’s <em><u>internal storage (e.g., its registers)</u></em>, the <em><u>operations (i.e., the instruction set)</u></em> that the computer can perform on data, and the <em><u>addressing modes</u></em> used to access data.




<h2>REGISTERS</h2>

A <em>register </em>is a storage device that holds a single data word exactly like a memory location. Registers are physically located in the CPU chip and can be accessed far more rapidly than memory. In principle, there’s no fundamental difference between a location in memory and a register. There are just a few registers in a computer, but millions of storage locations in memory. Consequently, you need far fewer bits to specify a register than a memory location.




<h2>IMPORTANT POINT</h2>

Never confuse the following two concepts: value and address (or location). A memory location holds a value which is the information stored in that location. The address of an item is where it is in memory and its value is what it is.




For example, suppose memory location 1234 contains the value 55. If we add 1 to 55 we get 55 + 1 which is 56. That is, we’ve changed the value of a variable. Now, if we add 1 to the address 1234, we get 1235. That’s a different location in memory which holds a different variable.




The reason for making this point is that it is all too easy to confuse these two concepts because of the way we learn algebra at high school. We use equations like <em>x = 4</em>. When we write programs that use variables, the variables usually refer to the locations of data not to the values. So, when we say <em>x = 4</em>, we actually mean that the memory location called <em>x</em> contains the value <em>4</em>.




<h2>QUICK OVERVIEW OF THE ARM</h2>

The ARM processor is classified as a 32-bit RISC (<em>reduced instruction set computer</em>) with a three-operand register-to-register instruction set. This is just a fancy way of saying that computer operations involve <em><u>three</u></em> operands in registers such as ADD <strong>r1</strong>,r2,r3. There are a few instructions that have <em><u>two</u></em> operands and some that have <em><u>four</u></em>, but that doesn’t change the overall classification.




In order to get data into and out of a register (transfers data between memory and register), there are two special instructions called <em>load</em> and <em>store</em>. <em>Load</em> (LDR) transfers data from memory to a register, while <em>store</em> (STR) transfers data from a register to memory. These instructions have the forms LDR <strong>r0</strong>,[r1] and STR r0,<strong>[r1]</strong>, respectively. These instructions use register indirect (i.e., pointer-based) addressing, where the location of the memory element to be accessed is held in a register. The register indirect addressing mode is indicated here by [r1].




The ARM uses a special instruction called ADR (<em>load register with an address</em>) that sets up a pointer to a place in the memory.




An ARM instruction like SUB <strong>r3</strong>,r2,#4 subtracts the actual value 4 (<em>remember that the literal is indicated by the # symbol</em>) from the contents of register r2 and puts the result in r3. Data operations implemented by ARM processors write the destination (result) operand first on the left. We write the destination operand in <strong>bold</strong> font to remind ourselves where the result goes.




<h2>SUB-WORD OPERATIONS</h2>

If you wish to access individual bytes in a 32-bit processor, you need special instructions. RISC processors do not (generally) support 8-bit or 16-bit <em>data-processing operations</em> on 32-bit registers, but they do support 8-bit and 16-bit <em>memory accesses</em>. Consider the following ARM examples.




LDR  <strong>r0</strong>,[r1] ;load r0 with the 32-bit contents of memory pointed @ by register r1

LDRB <strong>r0</strong>,[r1] ;load r0 with the  8-bit contents of memory pointed @ by register r1

LDRH <strong>r0</strong>,[r1] ;load r0 with the 16-bit contents of memory pointed @ by register r1

There is also a similar set of <em>store</em> mnemonics with the forms STR, STRB, and STRH.

STR  r0,<strong>[r1] </strong>;store the content      of r0 in memory pointed @ by register r1

STRB r0,<strong>[r1]</strong> ;store the LSB     byte of r0 in memory pointed @ by register r1 STRH r0,<strong>[r1] </strong>;store the LSB two byte of r0 in memory pointed @ by register r1




<h2>USING THE KEIL SIMULATOR</h2>

The processor in the PC is not a member of the ARM family. It’s usually a member of Intel’s IA32 family or an AMD processor. However, you can run ARM code processor on your PC using a program from Keil. The Keil package, called μVision4, is very sophisticated and is intended for engineers designing embedded ARM-based systems. Consequently, it includes far more facilities than we need. The demonstration version that you can download for a PC is limited to assemblylevel programs smaller than 32K bytes. This restriction is not a problem for students.

<h2>PROBLEM SET</h2>

Before you start practicing this lab, you need to review and fully understand how to use <em>the Keil ARM simulator</em>, which is covered in tutorial 4<em> (Tutorial_04_Introduction_to_ARM_Simulator.pdf).</em>

<ol>

 <li>Let’s create a very simple example.</li>

</ol>




MOV <strong>r1</strong>,#2    ;Put 2 in register r1

MOV <strong>r2</strong>,#3    ;Put 3 in register r2

ADD <strong>r0</strong>,r1,r2 ;Add r1 to r2 and put the result in r0




Note how simple the instructions are. Basically, each instruction performs one primitive operation.

Note also, the semicolon indicates the start of a comment field that is not part of the executable code.




Use the Keil simulator to write, assemble, and run the above program fragment.

Note that you will need to use appropriate assembly directives to make this program fragment a program.




Modify your program by initializing the values of r3, r4, and r5 by literals 4, 5, and 6, respectively. In addition, add together the five values in registers r1, r2, r3, r4, and r5. Store the result in r0. Do not forget to comment each line of your code

<ol start="2">

 <li>Write a program that includes <em>deliberate</em> syntax errors.</li>

</ol>

Enter it in the Keil simulator, assemble (build) it and attempt to fix these errors.

<ol start="3">

 <li>Write a simple program to perform: Z = A + B + C – (D × E). The instructions you may use are ADD, SUB, and MUL. Assume that the data are in registers r0 to r4 (representing A to E) and the result will be put in r5. You can use MOV instruction to initialize r0 to r4. Enter your program into the Keil simulator and run it. Try various values for A, B, C, D, and E <strong><em>Do you get the expected answer?</em></strong></li>

 <li>Now assume that A, B, C, D, E and Z are 32-bit values in memory. You can initialize them by using a DCD Remember, you can use a label to define the <em>first</em> location of a memory block. Note that, you can put multiple values after the directive DCD, DCB, or DCH, but you need to separate the values with commas. However, since each data item needs its own name, you are going to have to use one directive per element; e.g.,

  <ul>

   <li>DCD 4</li>

   <li>DCD 12</li>

   <li>DCD -2</li>

   <li>DCD -5</li>

   <li>DCD -9</li>

  </ul></li>

</ol>

Z   DCD  0

Modify your program in Q3 to load (LDR) the values of r0 to r4 using these A, B, C, D, and E values, respectively. You also need to store (STR) the result in location Z. <strong><em>Do you get the expected answer?</em></strong>




To see the content of a memory segment, you need to open a memory window. To do this, <em><u>while you are in the</u> <u>debugging</u></em> mode, click on <strong>View </strong>then select <strong>Memory Window </strong>and then <strong>Memory 1</strong>. Enter the starting address in the <strong>Address </strong>box in the memory window (which is 0) and hit return. In the memory window, we can see both the <em><u>code</u></em> and <em><u>data</u></em>. Note that, you may need to resize the memory window, by dragging the edge of the memory window to display as many or as few bytes per line as you want.




In Keil simulator, memory locations are <em>read-only</em>, by default. To change some of these locations to <em>read-write</em>, we have to perform an additional step. <em>Click</em> the <strong>Debug </strong>and then the <strong>Memory Map</strong> tabs. <em>Enter</em> a memory map range in the <strong>Map Range box </strong>and <em>check the box</em> <strong>Read,</strong> and<strong> Write, </strong><em><u>as needed</u></em>, and finally <em>click</em> on the<strong> Map Range button.</strong> The format of the range is defined as 0x000,0x200. This range is from memory location 0x000 to memory location 0x200.  <strong><em>This step must be performed each time you enter the debugging mode.</em></strong>

Without this step, you will <strong><em>NOT</em></strong> be able to successful <em>store</em> date in memory. 5. Now assume that A, B, C, D, E and Z are 8-bit values in memory. You can initialize them by using a DCB directive. Modify accordingly your code in Q4 to deal with these byte variables. <strong><em>Do you get the expected answer? Think of the overflow situations.</em></strong>