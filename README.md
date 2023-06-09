Download Link: https://assignmentchef.com/product/solved-comp1410-lab-8-file-processing-sequential-and-direct-access
<br>
<strong>Objective: </strong>In this Lab you will practice using sequential and direct access forms of writing and reading to and from a text (character based) file and a binary file.

<strong>PRELIMINARY NOTE: </strong>

There are two basic types of file processing, one involving character (or text) based data where the records are of variable length, in general.  The other kind of file contains records that are of fixed length and the types of data may be both character and machine (binary) representations.  This lab is divided into two parts.  When you are finished, you should be able to clearly distinguish the type of file and the different functions required to access records in each kind of file, as well as other aspects of files.

PART 1: Sequential Files

<u>Background</u>:

To process sequential text files in C, we use the header file &lt;stdio.h&gt; where various functions for file processing are defined. A few of them are:

<ol>

 <li>fopen (): to open a file,</li>

 <li>fclose (): to close a file,</li>

 <li>fscanf (): to read from a file, and</li>

 <li>fprintf (): to write into a file.</li>

</ol>

<strong>Work to do: <u>PART – 1A</u> </strong>

<strong>Writing into a Sequential File: </strong>

In this lab you will be using the structure (as defined below) and implement an interactive program capable of prompting the user and storing 3 employee records into a file called “employee.dat”.  Write a program called “Lab8a.c” that creates the file called “employee.dat”.  This “employee.dat” file will also be used in the second part of this laboratory exercise.




The format of the file would look like this sample (excluding the first line):




ID FIRSTNAME LASTNAME

10 john doe 64.5

20 mary jane 92.3

40 alice bower 54.0

30 jim smith 78.2




Instructions: Write a C program called “Lab8a.c” to accomplish the following: (The skeleton code is given below for your convenience. Use the 3 functions specified to perform the input, printing and saving the records to the file.)




<strong>#include &lt;stdio.h&gt; struct employee { char firstname[40]; char lastname[40]; </strong>

<strong>int id; int GPA; </strong>

<strong>}; </strong>

<strong>typedef struct employee Employee; </strong>

<strong> </strong>

<strong>/* Input the employee data interactively from the keyboard */ void InputEmpRecord(Employee *EmpList); </strong>

<strong> </strong>

<strong>/* Display the contents of Employee records from the list */ void PrintEmpList(const Employee *EmpList); </strong>

<strong> </strong>

<strong>/* Save the employee records from the list to the newly created text file specified by FileName */ </strong>

<strong>void SaveEmpList(const Employee *EmpList, const char *FileName); </strong>

<strong> </strong>

<strong>int main() { </strong>

<strong>Employee EmpList[3]; </strong>

<strong>InputEmpRecord(EmpList); </strong>

<strong>PrintEmpList(EmpList); </strong>

<strong>SaveEmpList(EmpList, “employee.dat”); return 0; </strong>

<strong>} </strong>




<strong><u>PART – 1B</u> </strong>

<strong>Reading from a Sequential File: </strong>

Write a different C program called “Lab8b.c” that reads the file “employee.dat” (from Part A above) containing the 3 records created in part A into an array called EmployeeList (of type employee, size 3). Then, write and use the WordCap(char *word) function to capitalize only the first letter of each of the first and last names of the 3 employee records. Then save the new records back to the “employee.dat” file, overwriting the old records.




Note: After you run program “Lab8b.c” you can use the command “cat employee.dat” to view the contents of the file and verify the results – you can also use a standard editor. The file now should look like this sample (excluding the first line):




ID FIRSTNAME LASTNAME

10 John Doe 64.5

20 Mary Jane 92.3

40 Alice Bower 54.0

30 Jim Smith 78.2







PART 2: Direct Access (Binary) Files

<u>Background</u>:.

To process direct access binary files in C, we use the header file &lt;stdio.h&gt; where various functions for file processing are defined. A few of them are:

<ol>

 <li>fopen (): to open a file,</li>

 <li>fclose (): to close a file,</li>

 <li>fread (): to read from a file, and</li>

 <li>fwrite (): to write into a file.</li>

 <li>fseek (): position the read-write head to a desired location for I/O</li>

</ol>

<strong> </strong>

<strong>Work to do: <u>PART – 2A</u> </strong>

<strong>Writing into a Direct Access File: </strong>

In this lab you will be using the structure (as defined below) and implement an interactive program capable of prompting the user and storing 3 employee records into a file called “employeeDA.dat” (DA is shorthand for Direct Access).  Write a program called “Lab8c.c” that creates the file called “employeeDA.dat”.  This file will also be used in the 2B part of this exercise.  Note that the input can come directly from the file “employee.dat” created in Part 1B.




The format of the file would look like this sample (excluding the first line):




ID FIRSTNAME LASTNAME GPA

10 John Doe 64.5

20 Mary Jane 92.3

40 Alice Bower 54.0

30 Jim Smith 78.2




Instructions: Write a C program called “Lab8c.c” to accomplish the following: (The skeleton code is given below for your convenience. Use the 3 functions specified to perform the input, printing and saving the records to the file.)




<strong>#include &lt;stdio.h&gt; struct employee { char firstname[40]; char lastname[40]; int id; float GPA; </strong>

<strong>}; </strong>

<strong>typedef struct employee Employee; </strong>

<strong> </strong>

<strong>/* Input the employee data interactively from the keyboard */ void InputEmpRecord(Employee *EmpList); </strong>

<strong> </strong>

<strong>/* Display the contents of Employee records from the list */ void PrintEmpList(const Employee *EmpList); </strong>

<strong> </strong>

<strong>/* Save the employee records from the list to the newly created binary file specified by FileName */ </strong>

<strong>void SaveEmpList(const Employee *EmpList, const char *FileName); </strong>

<strong> </strong>

<strong>int main() { </strong>

<strong>Employee EmpList[4]; </strong>

<strong>InputEmpRecord(EmpList); </strong>

<strong>PrintEmpList(EmpList); </strong>

<strong>SaveEmpList(EmpList, “employee.dat”); return 0; </strong>

<strong>} </strong>




Note that the function SaveEmpList() must perform opening of the file “employee.dat” for writing in binary mode, then writing all records, and finally closing the file.  Make sure that the character arrays used for first and last name are fully initialized (e.g. use ‘ ’) before writing to file (to ensure that all data fields hold initial data).




<strong><u>PART – 2B</u> </strong>

<strong>Reading and modifying data from a Direct Access File: </strong>

Write a different C program called “Lab8d.c” that performs an <em>in-place sort by GPA</em> of the data in “employee.dat”.  This means that the records in the file must be re-arranged, or sorted, using the GPA as the sorting key value.  You may not use an array to hold all file data.  You may only store records in at most <u>two</u> data structures within your program.  The records must be in order from highest to lowest GPA.  To prove if your program works, start by reading in each record and then outputting the information to the monitor (stdout) until encountering end-of-file; during this process you can determine the number of records in the file.  After closing and re-opening the file, perform a sort in much the same way that one sorts elements of an array – if two adjacent records are not in the correct order, then swap them.  Use a temporary structure to swap records.  You may use any algorithm for sorting.  Finally, after the sort is finished, once again output all records to show that they appear in sorted order.




Note: Students should examine the content of the file “employee.dat” to verify that not all information in each record is human-readable as characters/digits/punctuation.




Using the data given above, the final sorted file output should look like:




ID FIRSTNAME LASTNAME GPA

20 Mary Jane 92.3

30 Jim Smith 78.2

10 John Doe 64.5

40 Alice Bower 54.0