# CODEALPHA

       IDENTIFICATION DIVISION.                                         00010000
       PROGRAM-ID. CA11G189.                                            00020000
       ENVIRONMENT DIVISION.                                            00030000
       INPUT-OUTPUT SECTION.                                            00040000
       FILE-CONTROL.                                                    00050000
           SELECT TI001-INP ASSIGN TO INPSTDPS                          00060000
                     ORGANIZATION IS SEQUENTIAL                         00070000
                     ACCESS MODE IS SEQUENTIAL                          00080000
                     FILE STATUS IS WS-FILE-STATUS1.                    00090000
           SELECT MI001-OUT ASSIGN TO AS-OUTSTDES                       00100001
                     ORGANIZATION IS SEQUENTIAL                         00110000
                     ACCESS MODE IS SEQUENTIAL                          00120000
                     FILE STATUS IS WS-FILE-STATUS2.                    00130001
           SELECT MI002-ERR ASSIGN TO ERRSTDPS                          00140001
                     ORGANIZATION IS SEQUENTIAL                         00150000
                     ACCESS MODE IS SEQUENTIAL                          00160000
                     FILE STATUS IS WS-FILE-STATUS3.                    00170001
           SELECT MI003-EXL ASSIGN TO OUTSTDPS                          00180001
                     ORGANIZATION IS SEQUENTIAL                         00190000
                     ACCESS MODE IS SEQUENTIAL                          00200000
                     FILE STATUS IS WS-FILE-STATUS4.                    00210001
       DATA DIVISION.                                                   00220001
       FILE SECTION.                                                    00230001
      ******************************************************************00240001
      ********INPUT FILE DECLARATION                                    00250001
      ******************************************************************00260001
       FD TI001-INP.                                                    00270001
       01 TI001-INP-RECORD.                                             00280001
         05 TI001-STUDENT-NO     PIC X(05).                             00290001
         05 FILLER               PIC X(01).                             00300001
         05 TI001-STUDENT-GEN    PIC X(01).                             00310001
         05 FILLER               PIC X(01).                             00320001
         05 TI001-SUB-1          PIC 9(02).9(02).                       00330001
         05 FILLER               PIC X(01).                             00340001
         05 TI001-SUB-2          PIC 9(02).9(02).                       00350001
         05 FILLER               PIC X(01).                             00360001
         05 TI001-SUB-3          PIC 9(02).9(02).                       00370001
         05 FILLER               PIC X(55).                             00380001
       FD MI001-OUT.                                                    00390001
       01 MI001-OUT-RECORD.                                             00400001
         05 MI001-STUDENT-NO     PIC X(05).                             00410001
         05 FILLER               PIC X(75).                             00420010
       FD MI002-ERR.                                                    00430001
       01 MI002-ERR-RECORD.                                             00440001
         05 MI002-STUDENT-NO     PIC X(05).                             00450001
         05 FILLER               PIC X(01).                             00460001
         05 MI002-STUDENT-GEN    PIC X(01).                             00470001
         05 FILLER               PIC X(01).                             00480001
         05 MI002-SUB-1          PIC 9(02).9(02).                       00490001
         05 FILLER               PIC X(01).                             00500001
         05 MI002-SUB-2          PIC 9(02).9(02).                       00510001
         05 FILLER               PIC X(01).                             00520001
         05 MI002-SUB-3          PIC 9(02).9(02).                       00530001
         05 FILLER               PIC X(01).                             00540005
         05 MI002-ERR-FIELD      PIC X(15).                             00550001
         05 FILLER               PIC X(39).                             00560001
       FD MI003-EXL.                                                    00570001
       01 MI003-EXL-RECORD.                                             00580001
         05 MI003-STUDENT-NO     PIC X(05).                             00590001
         05 FILLER               PIC X(75).                             00600011
       WORKING-STORAGE SECTION.                                         00610001
       01 WMI001-OUT-RECORD.                                            00620010
         05 WMI001-STUDENT-NO     PIC X(05).                            00630010
         05 FILLER               PIC X(01) VALUE SPACES.                00640010
         05 MI001-STUDENT-GEN    PIC X(01).                             00650010
         05 FILLER               PIC X(01) VALUE SPACES.                00660010
         05 MI001-SUB-1          PIC 9(02).9(02).                       00670010
         05 FILLER               PIC X(01) VALUE SPACES.                00680010
         05 MI001-SUB-2          PIC 9(02).9(02).                       00690010
         05 FILLER               PIC X(01) VALUE SPACES.                00700010
         05 MI001-SUB-3          PIC 9(02).9(02).                       00710010
         05 FILLER               PIC X(01) VALUE SPACES.                00720010
         05 MI001-TOT-MARK       PIC 9(03).9(02).                       00730010
         05 FILLER               PIC X(01) VALUE SPACES.                00740010
         05 MI001-TOT-PER        PIC 9(03).                             00750010
         05 FILLER               PIC X(01) VALUE SPACES.                00760010
         05 MI001-GRADE          PIC X(01).                             00770010
         05 FILLER               PIC X(01) VALUE SPACES.                00780010
         05 MI001-LEVEL          PIC X(09).                             00790010
         05 FILLER               PIC X(01) VALUE SPACES.                00800010
         05 MI001-SCH-ELIG       PIC X(01).                             00810010
         05 FILLER               PIC X(30) VALUE SPACES.                00820010
       01 WMI003-EXL-RECORD.                                            00830011
         05 WMI003-STUDENT-NO     PIC X(05).                            00840011
         05 FILLER               PIC X(01) VALUE SPACES.                00850011
         05 MI003-STUDENT-GEN   PIC X(01).                              00860011
         05 FILLER               PIC X(01) VALUE SPACES.                00870011
         05 MI003-TOT-MARK       PIC 9(03).9(02).                       00880011
         05 FILLER               PIC X(01) VALUE SPACES.                00890011
         05 MI003-TOT-PER        PIC 9(03).                             00900011
         05 FILLER               PIC X(01) VALUE SPACES.                00910011
         05 MI003-LEVEL          PIC X(09).                             00920011
         05 FILLER               PIC X(52) VALUE SPACES.                00930011
       01 WS-G-STATUS-FILES.                                            00940008
         05 WS-FILE-STATUS1  PIC X(02).                                 00950008
           88 WFS1-SUCCESS     VALUE '00'.                              00960008
           88 WFS1-EOF         VALUE '10'.                              00970008
           88 WFS1-REC-NOT-FND VALUE '23'.                              00980008
         05 WS-FILE-STATUS2  PIC X(02).                                 00990008
           88 WFS2-SUCCESS     VALUE '00'.                              01000008
           88 WFS2-EOF         VALUE '10'.                              01010008
           88 WFS2-REC-NOT-FND VALUE '23'.                              01020008
         05 WS-FILE-STATUS3  PIC X(02).                                 01030008
           88 WFS3-SUCCESS     VALUE '00'.                              01040008
           88 WFS3-EOF         VALUE '10'.                              01050008
           88 WFS3-REC-NOT-FND VALUE '23'.                              01060008
         05 WS-FILE-STATUS4  PIC X(02).                                 01070008
           88 WFS4-SUCCESS     VALUE '00'.                              01080008
           88 WFS4-EOF         VALUE '10'.                              01090008
           88 WFS4-REC-NOT-FND VALUE '23'.                              01100008
      ************************************                              01110001
      ** TEMP VARIABLE DECLARATION************************************  01120001
      **************************                                        01130001
       01 WS-VARIABLES.                                                 01140001
          05 WS-SUB-1       PIC 9(02)V9(02).                            01150001
          05 WS-SUB-2       PIC 9(02)V9(02).                            01160001
          05 WS-SUB-3       PIC 9(02)V9(02).                            01170001
          05 WS1-TOT-MARK   PIC 9(03)V9(02).                            01180001
          05 WS1-TOT-PER    PIC 9(03).                                  01190001
          05 WS-LENGTH      PIC 9(03).                                  01200001
      ******************************************************************01210001
      *** ARRAY DECLARATION****************************************     01220001
      ***********************************************                   01230001
       01 WS-ARRAY.                                                     01240001
         05 WS-EXLARR      OCCURS 1 TO 100 TIMES DEPENDING ON WS-LENGTH 01250001
                           INDEXED BY WS-INX.                           01260001
         10 WS-STUDENT-NO  PIC X(05).                                   01270001
         10 FILLER         PIC X(01).                                   01280001
         10 WS-STUDENT-GEN PIC X(01).                                   01290001
         10 FILLER         PIC X(01).                                   01300001
         10 WS-TOT-MARK    PIC 9(03).9(02).                             01310001
         10 FILLER         PIC X(01).                                   01320001
         10 WS-TOT-PER     PIC 9(03).                                   01330001
         10 FILLER         PIC X(01).                                   01340001
         10 WS-LEVEL       PIC X(09).                                   01350001
         10 FILLER         PIC X(52).                                   01360001
       01 WS-HEADER.                                                    01370001
         05 FILLER         PIC X(10) VALUE 'STUDENT_ID'.                01380001
         05 FILLER         PIC X(01).                                   01390001
         05 FILLER         PIC X(11) VALUE 'STUDENT_GEN'.               01400001
         05 FILLER         PIC X(01).                                   01410001
         05 FILLER         PIC X(05) VALUE 'SUB_1'.                     01420001
         05 FILLER         PIC X(01).                                   01430001
         05 FILLER         PIC X(05) VALUE 'SUB_2'.                     01440001
         05 FILLER         PIC X(01).                                   01450001
         05 FILLER         PIC X(05) VALUE 'SUB_3'.                     01460001
         05 FILLER         PIC X(01).                                   01470001
         05 FILLER         PIC X(09) VALUE 'ERR_FIELD'.                 01480001
         05 FILLER         PIC X(30).                                   01490001
       PROCEDURE DIVISION.                                              01500002
       0000-MAIN-PARA.                                                  01510002
            PERFORM 1000-OPEN-PARA  THRU 1000-EXIT-PARA.                01520002
            PERFORM 2000-READ-PARA  THRU 2000-EXIT-PARA                 01530003
                                     UNTIL WFS1-EOF.                    01540003
            PERFORM 3000-CLOSE-PARA THRU 3000-EXIT-PARA.                01550002
            STOP RUN.                                                   01560002
       1000-OPEN-PARA.                                                  01570002
            OPEN INPUT TI001-INP                                        01580008
            EVALUATE TRUE                                               01590002
            WHEN WFS1-SUCCESS                                           01600002
               DISPLAY 'INPUT OPEN SUCCESSFULLY'                        01610002
            WHEN OTHER                                                  01620002
               DISPLAY ' IO ERROR ' WS-FILE-STATUS1                     01630002
            PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  01640002
            END-EVALUATE.                                               01650002
      *     OPEN I-O MI001-OUT                                          01660009
            OPEN OUTPUT MI001-OUT                                       01670009
            EVALUATE TRUE                                               01680002
            WHEN WFS2-SUCCESS                                           01690002
               DISPLAY 'ESDS OPEN SUCCESSFULLY'                         01700002
            WHEN OTHER                                                  01710002
               DISPLAY ' IO ERROR ' WS-FILE-STATUS2                     01720002
            PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  01730002
            END-EVALUATE.                                               01740002
            OPEN OUTPUT MI002-ERR                                       01750008
            EVALUATE TRUE                                               01760002
            WHEN WFS3-SUCCESS                                           01770002
               DISPLAY 'ERRORFILE OPEN SUCCESSFULLY'                    01780002
            WHEN OTHER                                                  01790002
               DISPLAY ' IO ERROR ' WS-FILE-STATUS3                     01800002
            PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  01810002
            END-EVALUATE.                                               01820002
            OPEN OUTPUT MI003-EXL                                       01830008
            EVALUATE TRUE                                               01840002
            WHEN WFS4-SUCCESS                                           01850002
               DISPLAY 'EXECL OPEN SUCCESSFULLY'                        01860002
            WHEN OTHER                                                  01870002
               DISPLAY ' IO ERROR ' WS-FILE-STATUS4                     01880002
            PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  01890002
            END-EVALUATE.                                               01900002
       1000-EXIT-PARA.                                                  01910002
            EXIT.                                                       01920002
       2000-READ-PARA.                                                  01930002
            READ TI001-INP                                              01940008
            EVALUATE TRUE                                               01950002
            WHEN WFS1-SUCCESS                                           01960002
               PERFORM 2100-VALIDATE-PARA THRU 2100-EXIT-PARA           01970002
               DISPLAY 'INPUT READ SUCCESSFULLY'                        01980002
            WHEN WFS1-EOF                                               01990002
               DISPLAY 'END OF FILE'                                    02000002
            WHEN WFS1-REC-NOT-FND                                       02010002
               DISPLAY 'RECORD NOT FOUND'                               02020002
            WHEN OTHER                                                  02030002
               DISPLAY ' IO ERROR ' WS-FILE-STATUS1                     02040002
            PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  02050002
            END-EVALUATE.                                               02060002
       2000-EXIT-PARA.                                                  02070002
            EXIT.                                                       02080002
       2100-VALIDATE-PARA.                                              02090002
           DISPLAY '2100-VALIDATE-PARA'                                 02100007
           IF(TI001-STUDENT-GEN IS GREATER THAN SPACE)                  02110003
           AND                                                          02120002
           ((TI001-SUB-1(1:2) IS NUMERIC) AND                           02130002
                                     (TI001-SUB-1(4:2) IS NUMERIC))     02140002
           AND                                                          02150002
           ((TI001-SUB-2(1:2) IS NUMERIC) AND                           02160002
                                     (TI001-SUB-2(4:2) IS NUMERIC))     02170002
           AND                                                          02180002
           ((TI001-SUB-3(1:2) IS NUMERIC) AND                           02190002
                                     (TI001-SUB-3(4:2) IS NUMERIC))     02200002
                    PERFORM 2200-CORRECT-PARA                           02210002
                       THRU 2200-CORRECT-PARA-EXIT                      02220002
           ELSE                                                         02230002
                    PERFORM 2300-ERROR-FILE-PARA                        02240002
                       THRU 2300-ERROR-FILE-PARA-EXIT                   02250002
           END-IF.                                                      02260002
       2100-EXIT-PARA.                                                  02270003
           EXIT.                                                        02280002
       2200-CORRECT-PARA.                                               02290002
           DISPLAY '2200-CORRECT-PARA'                                  02300007
           MOVE TI001-SUB-1 TO WS-SUB-1                                 02310002
           MOVE TI001-SUB-2 TO WS-SUB-2                                 02320002
           MOVE TI001-SUB-3 TO WS-SUB-3                                 02330002
           CALL 'SUBPGM' USING WS-SUB-1, WS-SUB-2, WS-SUB-3             02340003
                         BY CONTENT WS1-TOT-MARK, WS1-TOT-PER           02350003
           IF (WS1-TOT-PER <= 45)                                       02360002
              MOVE 'D' TO MI001-GRADE                                   02370002
              MOVE 'POOR' TO MI001-LEVEL                                02380002
           END-IF                                                       02390004
           IF((WS1-TOT-PER > 45) AND (WS1-TOT-PER <= 65))               02400002
              MOVE 'C' TO MI001-GRADE                                   02410002
              MOVE 'AVERAGE' TO MI001-LEVEL                             02420002
           END-IF                                                       02430004
           IF((WS1-TOT-PER > 65) AND (WS1-TOT-PER <= 85))               02440002
              MOVE 'B' TO MI001-GRADE                                   02450002
              MOVE 'GOOD' TO MI001-LEVEL                                02460002
           END-IF                                                       02470004
           IF(WS1-TOT-PER > 85)                                         02480002
              MOVE 'A' TO MI001-GRADE                                   02490002
              MOVE 'EXCELLENT' TO MI001-LEVEL                           02500002
           END-IF                                                       02510004
           IF(MI001-GRADE = 'A' AND WS1-TOT-PER > 90)                   02520002
              MOVE 'Y' TO MI001-SCH-ELIG                                02530002
           ELSE                                                         02540002
              MOVE 'N' TO MI001-SCH-ELIG                                02550002
           END-IF                                                       02560002
           MOVE WS1-TOT-MARK TO MI001-TOT-MARK                          02570002
           MOVE WS1-TOT-PER TO MI001-TOT-PER                            02580002
           MOVE TI001-STUDENT-NO TO MI001-STUDENT-NO, WMI001-STUDENT-NO 02590010
           MOVE TI001-STUDENT-GEN TO MI001-STUDENT-GEN                  02600002
           MOVE TI001-SUB-1 TO MI001-SUB-1                              02610002
           MOVE TI001-SUB-2 TO MI001-SUB-2                              02620002
           MOVE TI001-SUB-3 TO MI001-SUB-3                              02630002
           WRITE MI001-OUT-RECORD FROM WMI001-OUT-RECORD                02640010
      ******************************************************************02650002
      *ARRAR TO EXCEL FILE                                              02660002
      *******************************************                       02670002
           SET WS-INX TO 1                                              02680002
           MOVE MI001-STUDENT-NO TO WS-STUDENT-NO(WS-INX)               02690002
           MOVE MI001-STUDENT-GEN TO WS-STUDENT-GEN(WS-INX)             02700002
           MOVE MI001-TOT-MARK TO WS-TOT-MARK(WS-INX)                   02710002
           MOVE MI001-TOT-PER TO WS-TOT-PER(WS-INX)                     02720002
           MOVE MI001-LEVEL TO WS-LEVEL(WS-INX)                         02730002
           IF(MI001-LEVEL = 'EXCELLENT')                                02740002
             MOVE WS-STUDENT-NO(WS-INX) TO MI003-STUDENT-NO,            02750011
                                            WMI003-STUDENT-NO           02760011
             MOVE WS-STUDENT-GEN(WS-INX) TO MI003-STUDENT-GEN           02770002
             MOVE WS-TOT-MARK(WS-INX) TO MI003-TOT-MARK                 02780002
             MOVE WS-TOT-PER(WS-INX) TO MI003-TOT-PER                   02790002
             MOVE WS-LEVEL(WS-INX) TO MI003-LEVEL                       02800002
             WRITE MI003-EXL-RECORD FROM WMI003-EXL-RECORD              02810011
           END-IF                                                       02820002
           SET WS-INX UP BY 1.                                          02830002
       2200-CORRECT-PARA-EXIT.                                          02840002
           EXIT.                                                        02850002
       2300-ERROR-FILE-PARA.                                            02860002
           DISPLAY '2300-ERROR-FILE-PARA'                               02870007
           IF(TI001-STUDENT-GEN IS NOT GREATER THAN SPACES)             02880003
             MOVE 'STUDENT-GEN' TO MI002-ERR-FIELD                      02890002
           END-IF                                                       02900002
           IF((TI001-SUB-1(1:2) IS NOT NUMERIC) OR                      02910008
                               (TI001-SUB-1(4:2) IS NOT NUMERIC))       02920008
             MOVE 'SUB-1' TO MI002-ERR-FIELD                            02930002
           END-IF                                                       02940002
           IF((TI001-SUB-2(1:2) IS NOT NUMERIC) OR                      02950008
                                (TI001-SUB-2(4:2) IS NOT NUMERIC))      02960008
             MOVE 'SUB-2' TO MI002-ERR-FIELD                            02970002
           END-IF                                                       02980002
           IF((TI001-SUB-3(1:2) IS NOT NUMERIC) OR                      02990008
                                (TI001-SUB-3(4:2) IS NOT NUMERIC))      03000008
             MOVE 'SUB-3' TO MI002-ERR-FIELD                            03010002
           END-IF                                                       03020002
           MOVE TI001-STUDENT-NO TO MI002-STUDENT-NO                    03030008
           MOVE TI001-STUDENT-GEN TO MI002-STUDENT-GEN                  03040008
           MOVE TI001-SUB-1 TO MI002-SUB-1                              03050002
           MOVE TI001-SUB-2 TO MI002-SUB-2                              03060002
           MOVE TI001-SUB-3 TO MI002-SUB-3                              03070002
             WRITE MI002-ERR-RECORD FROM WS-HEADER.                     03080013
       2300-ERROR-FILE-PARA-EXIT.                                       03090002
            EXIT.                                                       03100002
       3000-CLOSE-PARA.                                                 03110002
            CLOSE TI001-INP.                                            03120003
            EVALUATE TRUE                                               03130002
            WHEN WFS1-SUCCESS                                           03140002
               DISPLAY 'CLOSE SUCCESSFULLY'                             03150002
            WHEN OTHER                                                  03160002
               DISPLAY ' IO ERROR ' WS-FILE-STATUS1                     03170002
            PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  03180002
            END-EVALUATE.                                               03190002
            CLOSE MI001-OUT.                                            03200002
            EVALUATE TRUE                                               03210002
            WHEN WFS2-SUCCESS                                           03220002
               DISPLAY 'ESDS CLOSE SUCCESSFULLY'                        03230002
            WHEN OTHER                                                  03240002
               DISPLAY ' IO ERROR ' WS-FILE-STATUS2                     03250002
            PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  03260002
            END-EVALUATE.                                               03270002
            CLOSE MI002-ERR.                                            03280002
            EVALUATE TRUE                                               03290002
            WHEN WFS3-SUCCESS                                           03300002
               DISPLAY 'ERRORFILE CLOSE SUCCESSFULLY'                   03310002
            WHEN OTHER                                                  03320002
               DISPLAY ' IO ERROR ' WS-FILE-STATUS3                     03330002
            PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  03340002
            END-EVALUATE.                                               03350002
            CLOSE MI003-EXL.                                            03360002
            EVALUATE TRUE                                               03370002
            WHEN WFS4-SUCCESS                                           03380002
               DISPLAY 'EXECL CLOSE SUCCESSFULLY'                       03390002
            WHEN OTHER                                                  03400002
               DISPLAY ' IO ERROR ' WS-FILE-STATUS4                     03410002
            PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  03420002
            END-EVALUATE.                                               03430002
       3000-EXIT-PARA.                                                  03440002
            EXIT.                                                       03450002
       9000-TERMINATE-PARA.                                             03460002
       9000-EXIT.                                                       03470002
            EXIT.                                                       03480002




       IDENTIFICATION DIVISION.                                         00010000
       PROGRAM-ID. SUBPGM.                                              00020000
       ENVIRONMENT DIVISION.                                            00030000
       DATA DIVISION.                                                   00040000
       FILE SECTION.                                                    00050000
       WORKING-STORAGE SECTION.                                         00060000
       01 WS-VARIABLES.                                                 00070000
          05 WS-SUB-1     PIC 9(02)V9(02).                              00080000
          05 WS-SUB-2     PIC 9(02)V9(02).                              00090000
          05 WS-SUB-3     PIC 9(02)V9(02).                              00100000
          05 WS1-TOT-MARK PIC 9(03)V9(02).                              00110000
          05 WS1-TOT-PER  PIC 9(03).                                    00120000
       LINKAGE SECTION.                                                 00130000
       01 LS-VARIABLES.                                                 00140000
       05 LS-SUB-1  PIC 9(02)V9(02).                                    00150000
       05 LS-SUB-2  PIC 9(02)V9(02).                                    00160000
       05 LS-SUB-3  PIC 9(02)V9(02).                                    00170000
       05 LS-TOT-MARK PIC 9(03)V9(02).                                  00180000
       05 LS-TOT-PER PIC 9(03).                                         00190000
       PROCEDURE DIVISION USING LS-VARIABLES.                           00200000
       0000-MAIN-PARA.                                                  00210000
           COMPUTE LS-TOT-MARK ROUNDED = LS-SUB-1 + LS-SUB-2 + LS-SUB-3 00220000
           COMPUTE LS-TOT-PER = (LS-TOT-MARK / 300) * 100               00230000
           GOBACK.                                                      00240000
       0000-EXIT.                                                       00250000
           EXIT.                                                        00260000
