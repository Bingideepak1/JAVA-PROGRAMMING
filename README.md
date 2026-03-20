# CODEALPHA
MINI CASE STUDY: NEW STUDENT
STEP1: ISPF
o	Allocate a PS dataset with record length 80 with naming convention as below.
PS1 - <USERID>.L1L.STUDENT.PS1
o	   Using the details from below file layout, enter records into the PS1 file as per the instructions given,
o	Do not enter 1st row in PS file. 1st row contains header details for reference.
o	Do not enter 2nd row in PS file. 2nd row contains layout details for reference.
o	One space filler had to be inserted between each field in the PS file.     
o	All alphanumeric data to be entered in CAPITAL letters.         

 <img width="927" height="528" alt="image" src="https://github.com/user-attachments/assets/bfdded71-1068-426e-8705-a11287ebd70e" />


 STEP2: JCL
1.   JCL member naming convension JA11L<yyy>, where <yyy> denotes last 3 digits of your user ID. Proper JOB card without any RESTART step to be given.
o	Allocate a VSAM ESDS dataset with the following specifications,
RECORDSIZE (80, 80)
Name: <USERID>.L1L.STUDENT.ESDS
o	
STEP3:  JCL            
1.  JCL member naming convention JA21L<yyy>, where <yyy> denotes last 3 digits of your user ID. Proper JOB card without any RESTART step to be given.
o	Using Sort utility perform the below operations on PS1 and store the output in PS2 file. First step in this job should be the DELETE step for PS2 file.
PS1 -> <USERID>.L1L.STUDENT.PS1.
PS2 -> <USERID>.L1L.STUDENT.PS2.
                      i.    Sort records in ascending order based on Student_No.
                      ii.    Include records only which have Student _No starting with ‘S’.
                      iii.    Remove duplicates for each Student_No.
[Ex : If Student No SO441 contains 3 records after sorting, write the first record Alone to output file]
2.      Step1:Split the PS2 file into two equal parts(PS3 &PS4). The layout for the two new files will be the same as the PS2 file layout.
PS3 -> <USERID>.L1L.STUDENT.PS3
PS4 -> <USERID>.L1L.STUDENT.PS4
         Ex: If the PS2 file has 6 records , then records1,3 5 should come to PS3 file and the records 2,4,6 should come to PS4 file.
        Step2: Insert a word ‘SPLIT’ at 27th column of both the files. The Job steps have to be stored in JA31L<yyy>.Execute Step2, only if Step1 is ended successfully. Use COND codes to achieve this.
First step should be the delete step for the PS3 &PS4 files.
Sample record:
S1001 M 80.00 65.00 55.00 SPILT
S1006 F 50.00 64.00 59.00 SPILT
Filler Details: - One space between each field.
  
<img width="696" height="103" alt="image" src="https://github.com/user-attachments/assets/01fa78e1-a73c-448c-8a6e-daafa5a18434" />

STEP4: COBOL
 
Input file to be used in the program        : <USERID>.L1L.STUDENT.PS2
            DD name to be used                           : INPSTDPS
Output file to be used in the program     : <USERID>.L1L.STUDENT.ESDS
           DD name to be used                            : OUTSTDES
Output file to be used in the program     : <USERID>.L1L.STUDENT.ERR
           DD name to be used                            : ERRSTDPS
Output file to be used in the program     : <USERID>.L1K.STUDENT.EXCEL
           DD name to be used                            : OUTSTDPS
Note: Please use only the above-mentioned DD names. 
Write a COBOL program to perform the following,
o	Read records from input PS2 dataset (<USERID>.L1L.STUDENT.PS2) and validate input values for each field in the input file.
o	Check whether STUDENT_GEN field is not blank.
o	Check whether SUB_1 is numeric before and after decimal point.
o	Check whether SUB_2 is numeric before and after decimal point
o	Check whether SUB_3 is numeric before and after decimal point.
o	If the input record does not pass through the validations specified above successfully, then write that input record into error PS file <USERID>.L1L.STUDENT.ERR and start processing the next record.
o	Layout of ERROR file is as below.
o	The first record must be a header record with required spacing between the fields as mentioned below.
<img width="876" height="91" alt="image" src="https://github.com/user-attachments/assets/dcade3a2-47eb-45f9-a218-375be46b28e9" />



     
           Note : One space filler to be inserted between each field.
o	ERR_FIELD contains the error field name.
Ex:If the  Sub_1 field is not numeric, then the ERR_FIELD should contain ‘SUB-1’
If Student_Gen is blank,  then the ERR_FIELD should contain ‘STUDENT-GEN’
o	Do the following processing for every record which has passed through the validations successfully. 
o	
1.	Total marks and Percentage calculation

o	Using a sub-program, calculate TOT_MARK and Percentage using below formula  
TOT_MARK value should be rounded off to two decimal places.
         TOT_MARK=Sub_1+ Sub_2 + Sub_3
         TOT_PER = (TOT_MARK/ 300) * 100                 
                 
              Note : Suppress the leading zeroes of TOT_PER while writing to output file.
o	Return the values of TOT_MARK and TOT_PER to the main program.
 
o	Do the following two calculations in the Main program.

2. Calculation of  Grade and Level
o	For Students with TOT_PER <= 45
o	Write GRADE of corresponding record as ‘D’ and LEVEL as ‘POOR’
o	For Students with TOT_PER > 45 <=65
o	Write GRADE of corresponding record as ‘C’ and LEVEL as ‘AVERAGE’
o	For Students with TOT_PER > 65 <=85
o	Write GRADE of corresponding record as ‘B’ and LEVEL as ‘GOOD’
o	For Students with TOT_PER > 85
o	Write GRADE of corresponding record as ‘A’ and LEVEL as ‘EXCELLENT’

3.   Calculation of  Scholarship Eligible students
o	For Students with GRADE as A and TOT_PER > 90
o	Write SCH_ELIG of corresponding record as ‘Y’ .
o	For all other records
o	Write SCH_ELIG of corresponding record as ‘N’ .

o	Write output record into ESDS file in the below format.
<img width="940" height="77" alt="image" src="https://github.com/user-attachments/assets/23f2ff08-d640-4d71-8eba-a9f691a4f32b" />


  
One space filler to be inserted between each field.
TOT_PER should be displayed after suppressing the leading zeroes. 
Ex: ‘096’ should be displayed as ‘ 96’ 
o	Load the fields student No, Student Gender, Total marks, Total percentage, Level into a COBOL one dimensional table. The layout of the table for reference is given below:
<img width="621" height="93" alt="image" src="https://github.com/user-attachments/assets/c3191779-7e94-428f-8f09-1f46596044b0" />



  
        Note: TOT_PER should be displayed after suppressing the leading zeroes.
o	Find the records with level  = ‘EXCELLENT’ in the COBOL one dimensional table loaded in previous step.
o	Write all records having Level=’EXCELLENT’ into PS file 
<USERID>.L1L.STUDENT.EXCEL

Note: Layout of the PS files should be same as table layout mentioned above.
          One space filler to be inserted between each field.
o	Compile and run the above COBOL program to achieve the results.
JCL Member Naming Convention: JA41L<yyy>, where <yyy> denotes the last 3 digits of your user ID. Proper JOB card without any RESTART step to be given.
INSTRUCTIONS:
o	Follow the proper coding standards.
o	Provide proper error handling routines.
o	Place all the final deliverables into the PDS dataset :  ‘<USERID>.<X>.<Y>.PDS’ .
Where X ->  L1 and Y denotes 8 digit Batch name. Example:  Y- CHNMJ001
               [Example of L1 PDS              – TECN001.L1.CHNMJ001.PDS]
               
 For JCL’s, the member name should be “JA<x>1G<yyy>”
Note: Where <x> denotes the member no.(1 for 1st, 2 for 2nd member) and <yyy> denotes the last 3 digits of your user ID.
o	JCL's should be named in the member names as suggested in the respective steps.               
o	For COBOL Program, the member name should be “CA<x>1G<yyy>”
Note: Where <x> denotes the member no. (1 for 1st, 2 for 2nd member) and <yyy> denotes the last 3 digits of your user ID.
If there are 2 members for a COBOL (Main program and sub program) created by ID TECN001, the member name should be “CA11G001” and”CA21G001”.   
 
EXPECTED DELIVERABLES in Mainframe PDS ‘<USERID>.<X>.<Y>.PDS
’:
o	JCL for STEP2 and STEP3 in member names suggested in steps.
o	COBOL programs in member names suggested.
o	RUNJCL for the COBOL program.
