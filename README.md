#CODEALPHA.
1.	What are the 3 main JCL statements
2.	What are the different parameters in job statements?
3.	How will you verify the JCL without executing the steps?
4.	Explain in detail DISP parameters
5.	Explain in detail DCB parameters
6.	Explain in detail SPACE parameters
7.	Create a jcl with 1 step to allocate a PS file with recl=50 characters. (write the jcl in a fresh notepad)
8.	If the SPACE parameter is given as SPACE=(CYL,(5,2)), how many maximum cylinders will be allocated for the dataset.
9.	What are the DD names of input and output files in IEBGENER
10.	What is the difference between IEBGENER and IEBCOPY
11.	Write a JCL to copy member1 and member3 from tecn###.mylib.pds1 to tecn###.mylib.pds2 (write the jcl in a notepad)
12.	You have a sequential file with records of length 80. Sort the file based on employee ID (posi on 1 5) in ascending order (write the jcl in a notepad)
13.	(write the sort statement/sysin in the notepad) You have an input file with the following structure: 
Customer ID  		position 1-5 
Region			position 6-10
Sales amount		position 11-15 (packed decimal)
Find the sum of sales per region
14.	(write the step in the notepad) You have an input file with the following structure: 
Customer ID  		position 1-5 
Name			position 6-20
Status			position 21
If Status = ‘A’ write into active file and  if it is ‘I’ write into Inactive file
15.	If you encounter S013 error in SORT, what does it mean?

 

GDGs (Generation Data Groups) 

What is a GDG in mainframe systems, and why is it used? 

How do you define a GDG base using JCL? 

If there is a GDG base created with 4 as limit with SCRATCH/NO EMPTY option, what happens the 6th generation is created. 

Write a JCL to create 3 new versions of a sample GDG (gdg base name: userid.sample.gdg, FB, 80 chars) in one step using IEFBR14. (Write in a notepad) 

How will you refer to the previous generation in a JCL? 

Shape 

⚙️ Procedures (JCL Procedures) 

What is the purpose of a procedure in JCL, and how does it improve efficiency? 

What is the difference between an in-stream procedure and a cataloged procedure? 

Can you explain how symbolic parameters are used in procedures? 

If suppose there is a SYSIN DD in step1 of a procedure named PROC1, and I want to override it in the calling jcl program, how can I do it? (write in a notepad) 

Shape 

 

📦 VSAM (Virtual Storage Access Method) 

What are the different types of VSAM files? 

 

What is the difference between a Physical Sequential file and KSDS file? 

 

Write the define statement for creating an RRDS file? How will you modify this statement to create a KSDS file. (write in notepad) 

 

 How will you load data from a PS file into a VSAM file? 

 

What is the IDCAMs command used to read a record or range of records from a VSAM file. Give syntax for KSDS, RRDS and ESDS (Write in notepad) 

Shape 

🔑 Alternate Index (AIX) 

What is an Alternate Index in VSAM, and why is it used? 

 

What are the different steps involved in defining and using an alternate index? (write in a notepad, as much as they know. They might either just list down the steps and if comfortable they can explain using a sample KSDS) 

 

 
