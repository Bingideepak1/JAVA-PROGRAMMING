# CODEALPHA

000100 IDENTIFICATION DIVISION.                                         00010000
000200 PROGRAM-ID. CA11G189.                                            00020000
000300 ENVIRONMENT DIVISION.                                            00030000
000400 INPUT-OUTPUT SECTION.                                            00040000
000500 FILE-CONTROL.                                                    00050000
000600     SELECT TI001-INP ASSIGN TO INPSTDPS                          00060000
000700               ORGANIZATION IS SEQUENTIAL                         00070000
000800               ACCESS MODE IS SEQUENTIAL                          00080000
000900               FILE STATUS IS WS-FILE-STATUS1.                    00090000
001000     SELECT MI001-OUT ASSIGN TO AS-OUTSTDES                       00100001
001100               ORGANIZATION IS SEQUENTIAL                         00110000
001200               ACCESS MODE IS SEQUENTIAL                          00120000
001300               FILE STATUS IS WS-FILE-STATUS2.                    00130001
001400     SELECT MI002-ERR ASSIGN TO ERRSTDPS                          00140001
001500               ORGANIZATION IS SEQUENTIAL                         00150000
001600               ACCESS MODE IS SEQUENTIAL                          00160000
001700               FILE STATUS IS WS-FILE-STATUS3.                    00170001
001800     SELECT MI003-EXL ASSIGN TO OUTSTDPS                          00180001
001900               ORGANIZATION IS SEQUENTIAL                         00190000
002000               ACCESS MODE IS SEQUENTIAL                          00200000
002100               FILE STATUS IS WS-FILE-STATUS4.                    00210001
002200 DATA DIVISION.                                                   00220001
002300 FILE SECTION.                                                    00230001
002400******************************************************************00240001
002500********INPUT FILE DECLARATION                                    00250001
002600******************************************************************00260001
002700 FD TI001-INP.                                                    00270001
002800 01 TI001-INP-RECORD.                                             00280001
002900   05 TI001-STUDENT-NO     PIC X(05).                             00290001
003000   05 FILLER               PIC X(01).                             00300001
003100   05 TI001-STUDENT-GEN    PIC X(01).                             00310001
003200   05 FILLER               PIC X(01).                             00320001
003300   05 TI001-SUB-1          PIC 9(02).9(02).                       00330001
003400   05 FILLER               PIC X(01).                             00340001
003500   05 TI001-SUB-2          PIC 9(02).9(02).                       00350001
003600   05 FILLER               PIC X(01).                             00360001
003700   05 TI001-SUB-3          PIC 9(02).9(02).                       00370001
003800   05 FILLER               PIC X(55).                             00380001
003900 FD MI001-OUT.                                                    00390001
004000 01 MI001-OUT-RECORD.                                             00400001
004100   05 MI001-STUDENT-NO     PIC X(05).                             00410001
004200   05 FILLER               PIC X(75).                             00420010
004300 FD MI002-ERR.                                                    00430001
004400 01 MI002-ERR-RECORD.                                             00440001
004500   05 MI002-STUDENT-NO     PIC X(05).                             00450001
004600   05 FILLER               PIC X(01).                             00460001
004700   05 MI002-STUDENT-GEN    PIC X(01).                             00470001
004800   05 FILLER               PIC X(01).                             00480001
004900   05 MI002-SUB-1          PIC 9(02).9(02).                       00490001
005000   05 FILLER               PIC X(01).                             00500001
005100   05 MI002-SUB-2          PIC 9(02).9(02).                       00510001
005200   05 FILLER               PIC X(01).                             00520001
005300   05 MI002-SUB-3          PIC 9(02).9(02).                       00530001
005400   05 FILLER               PIC X(01).                             00540005
005500   05 MI002-ERR-FIELD      PIC X(15).                             00550001
005600   05 FILLER               PIC X(39).                             00560001
005700 FD MI003-EXL.                                                    00570001
005800 01 MI003-EXL-RECORD.                                             00580001
005900   05 MI003-STUDENT-NO     PIC X(05).                             00590001
006000   05 FILLER               PIC X(75).                             00600011
006100 WORKING-STORAGE SECTION.                                         00610001
006200 01 WMI001-OUT-RECORD.                                            00620010
006300   05 WMI001-STUDENT-NO     PIC X(05).                            00630010
006400   05 FILLER               PIC X(01) VALUE SPACES.                00640010
006500   05 MI001-STUDENT-GEN    PIC X(01).                             00650010
006600   05 FILLER               PIC X(01) VALUE SPACES.                00660010
006700   05 MI001-SUB-1          PIC 9(02).9(02).                       00670010
006800   05 FILLER               PIC X(01) VALUE SPACES.                00680010
006900   05 MI001-SUB-2          PIC 9(02).9(02).                       00690010
007000   05 FILLER               PIC X(01) VALUE SPACES.                00700010
007100   05 MI001-SUB-3          PIC 9(02).9(02).                       00710010
007200   05 FILLER               PIC X(01) VALUE SPACES.                00720010
007300   05 MI001-TOT-MARK       PIC 9(03).9(02).                       00730010
007400   05 FILLER               PIC X(01) VALUE SPACES.                00740010
007500   05 MI001-TOT-PER        PIC 9(03).                             00750010
007600   05 FILLER               PIC X(01) VALUE SPACES.                00760010
007700   05 MI001-GRADE          PIC X(01).                             00770010
007800   05 FILLER               PIC X(01) VALUE SPACES.                00780010
007900   05 MI001-LEVEL          PIC X(09).                             00790010
008000   05 FILLER               PIC X(01) VALUE SPACES.                00800010
008100   05 MI001-SCH-ELIG       PIC X(01).                             00810010
008200   05 FILLER               PIC X(30) VALUE SPACES.                00820010
008300 01 WMI003-EXL-RECORD.                                            00830011
008400   05 WMI003-STUDENT-NO     PIC X(05).                            00840011
008500   05 FILLER               PIC X(01) VALUE SPACES.                00850011
008600   05 MI003-STUDENT-GEN   PIC X(01).                              00860011
008700   05 FILLER               PIC X(01) VALUE SPACES.                00870011
008800   05 MI003-TOT-MARK       PIC 9(03).9(02).                       00880011
008900   05 FILLER               PIC X(01) VALUE SPACES.                00890011
009000   05 MI003-TOT-PER        PIC 9(03).                             00900011
009100   05 FILLER               PIC X(01) VALUE SPACES.                00910011
009200   05 MI003-LEVEL          PIC X(09).                             00920011
009300   05 FILLER               PIC X(52) VALUE SPACES.                00930011
009400 01 WS-G-STATUS-FILES.                                            00940008
009500   05 WS-FILE-STATUS1  PIC X(02).                                 00950008
009600     88 WFS1-SUCCESS     VALUE '00'.                              00960008
009700     88 WFS1-EOF         VALUE '10'.                              00970008
009800     88 WFS1-REC-NOT-FND VALUE '23'.                              00980008
009900   05 WS-FILE-STATUS2  PIC X(02).                                 00990008
010000     88 WFS2-SUCCESS     VALUE '00'.                              01000008
010100     88 WFS2-EOF         VALUE '10'.                              01010008
010200     88 WFS2-REC-NOT-FND VALUE '23'.                              01020008
010300   05 WS-FILE-STATUS3  PIC X(02).                                 01030008
010400     88 WFS3-SUCCESS     VALUE '00'.                              01040008
010500     88 WFS3-EOF         VALUE '10'.                              01050008
010600     88 WFS3-REC-NOT-FND VALUE '23'.                              01060008
010700   05 WS-FILE-STATUS4  PIC X(02).                                 01070008
010800     88 WFS4-SUCCESS     VALUE '00'.                              01080008
010900     88 WFS4-EOF         VALUE '10'.                              01090008
011000     88 WFS4-REC-NOT-FND VALUE '23'.                              01100008
011100************************************                              01110001
011200** TEMP VARIABLE DECLARATION************************************  01120001
011300**************************                                        01130001
011400 01 WS-VARIABLES.                                                 01140001
011500    05 WS-SUB-1       PIC 9(02)V9(02).                            01150001
011600    05 WS-SUB-2       PIC 9(02)V9(02).                            01160001
011700    05 WS-SUB-3       PIC 9(02)V9(02).                            01170001
011800    05 WS1-TOT-MARK   PIC 9(03)V9(02).                            01180001
011900    05 WS1-TOT-PER    PIC 9(03).                                  01190001
012000    05 WS-LENGTH      PIC 9(03).                                  01200001
012100******************************************************************01210001
012200*** ARRAY DECLARATION****************************************     01220001
012300***********************************************                   01230001
012400 01 WS-ARRAY.                                                     01240001
012500   05 WS-EXLARR      OCCURS 1 TO 100 TIMES DEPENDING ON WS-LENGTH 01250001
012600                     INDEXED BY WS-INX.                           01260001
012700   10 WS-STUDENT-NO  PIC X(05).                                   01270001
012800   10 FILLER         PIC X(01).                                   01280001
012900   10 WS-STUDENT-GEN PIC X(01).                                   01290001
013000   10 FILLER         PIC X(01).                                   01300001
013100   10 WS-TOT-MARK    PIC 9(03).9(02).                             01310001
013200   10 FILLER         PIC X(01).                                   01320001
013300   10 WS-TOT-PER     PIC 9(03).                                   01330001
013400   10 FILLER         PIC X(01).                                   01340001
013500   10 WS-LEVEL       PIC X(09).                                   01350001
013600   10 FILLER         PIC X(52).                                   01360001
013700 01 WS-HEADER.                                                    01370001
013800   05 FILLER         PIC X(10) VALUE 'STUDENT_ID'.                01380001
013900   05 FILLER         PIC X(01).                                   01390001
014000   05 FILLER         PIC X(11) VALUE 'STUDENT_GEN'.               01400001
014100   05 FILLER         PIC X(01).                                   01410001
014200   05 FILLER         PIC X(05) VALUE 'SUB_1'.                     01420001
014300   05 FILLER         PIC X(01).                                   01430001
014400   05 FILLER         PIC X(05) VALUE 'SUB_2'.                     01440001
014500   05 FILLER         PIC X(01).                                   01450001
014600   05 FILLER         PIC X(05) VALUE 'SUB_3'.                     01460001
014700   05 FILLER         PIC X(01).                                   01470001
014800   05 FILLER         PIC X(09) VALUE 'ERR_FIELD'.                 01480001
014900   05 FILLER         PIC X(30).                                   01490001
015000 PROCEDURE DIVISION.                                              01500002
015100 0000-MAIN-PARA.                                                  01510002
015200      PERFORM 1000-OPEN-PARA  THRU 1000-EXIT-PARA.                01520002
015300      PERFORM 2000-READ-PARA  THRU 2000-EXIT-PARA                 01530003
015400                               UNTIL WFS1-EOF.                    01540003
015500      PERFORM 3000-CLOSE-PARA THRU 3000-EXIT-PARA.                01550002
015600      STOP RUN.                                                   01560002
015700 1000-OPEN-PARA.                                                  01570002
015800      OPEN INPUT TI001-INP                                        01580008
015900      EVALUATE TRUE                                               01590002
016000      WHEN WFS1-SUCCESS                                           01600002
016100         DISPLAY 'INPUT OPEN SUCCESSFULLY'                        01610002
016200      WHEN OTHER                                                  01620002
016300         DISPLAY ' IO ERROR ' WS-FILE-STATUS1                     01630002
016400      PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  01640002
016500      END-EVALUATE.                                               01650002
016600*     OPEN I-O MI001-OUT                                          01660009
016700      OPEN OUTPUT MI001-OUT                                       01670009
016800      EVALUATE TRUE                                               01680002
016900      WHEN WFS2-SUCCESS                                           01690002
017000         DISPLAY 'ESDS OPEN SUCCESSFULLY'                         01700002
017100      WHEN OTHER                                                  01710002
017200         DISPLAY ' IO ERROR ' WS-FILE-STATUS2                     01720002
017300      PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  01730002
017400      END-EVALUATE.                                               01740002
017500      OPEN OUTPUT MI002-ERR                                       01750008
017600      EVALUATE TRUE                                               01760002
017700      WHEN WFS3-SUCCESS                                           01770002
017800         DISPLAY 'ERRORFILE OPEN SUCCESSFULLY'                    01780002
017900      WHEN OTHER                                                  01790002
018000         DISPLAY ' IO ERROR ' WS-FILE-STATUS3                     01800002
018100      PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  01810002
018200      END-EVALUATE.                                               01820002
018300      OPEN OUTPUT MI003-EXL                                       01830008
018400      EVALUATE TRUE                                               01840002
018500      WHEN WFS4-SUCCESS                                           01850002
018600         DISPLAY 'EXECL OPEN SUCCESSFULLY'                        01860002
018700      WHEN OTHER                                                  01870002
018800         DISPLAY ' IO ERROR ' WS-FILE-STATUS4                     01880002
018900      PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  01890002
019000      END-EVALUATE.                                               01900002
019100 1000-EXIT-PARA.                                                  01910002
019200      EXIT.                                                       01920002
019300 2000-READ-PARA.                                                  01930002
019400      READ TI001-INP                                              01940008
019500      EVALUATE TRUE                                               01950002
019600      WHEN WFS1-SUCCESS                                           01960002
019700         PERFORM 2100-VALIDATE-PARA THRU 2100-EXIT-PARA           01970002
019800         DISPLAY 'INPUT READ SUCCESSFULLY'                        01980002
019900      WHEN WFS1-EOF                                               01990002
020000         DISPLAY 'END OF FILE'                                    02000002
020100      WHEN WFS1-REC-NOT-FND                                       02010002
020200         DISPLAY 'RECORD NOT FOUND'                               02020002
020300      WHEN OTHER                                                  02030002
020400         DISPLAY ' IO ERROR ' WS-FILE-STATUS1                     02040002
020500      PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  02050002
020600      END-EVALUATE.                                               02060002
020700 2000-EXIT-PARA.                                                  02070002
020800      EXIT.                                                       02080002
020900 2100-VALIDATE-PARA.                                              02090002
021000     DISPLAY '2100-VALIDATE-PARA'                                 02100007
021100     IF(TI001-STUDENT-GEN IS GREATER THAN SPACE)                  02110003
021200     AND                                                          02120002
021300     ((TI001-SUB-1(1:2) IS NUMERIC) AND                           02130002
021400                               (TI001-SUB-1(4:2) IS NUMERIC))     02140002
021500     AND                                                          02150002
021600     ((TI001-SUB-2(1:2) IS NUMERIC) AND                           02160002
021700                               (TI001-SUB-2(4:2) IS NUMERIC))     02170002
021800     AND                                                          02180002
021900     ((TI001-SUB-3(1:2) IS NUMERIC) AND                           02190002
022000                               (TI001-SUB-3(4:2) IS NUMERIC))     02200002
022100              PERFORM 2200-CORRECT-PARA                           02210002
022200                 THRU 2200-CORRECT-PARA-EXIT                      02220002
022300     ELSE                                                         02230002
022400              PERFORM 2300-ERROR-FILE-PARA                        02240002
022500                 THRU 2300-ERROR-FILE-PARA-EXIT                   02250002
022600     END-IF.                                                      02260002
022700 2100-EXIT-PARA.                                                  02270003
022800     EXIT.                                                        02280002
022900 2200-CORRECT-PARA.                                               02290002
023000     DISPLAY '2200-CORRECT-PARA'                                  02300007
023100     MOVE TI001-SUB-1 TO WS-SUB-1                                 02310002
023200     MOVE TI001-SUB-2 TO WS-SUB-2                                 02320002
023300     MOVE TI001-SUB-3 TO WS-SUB-3                                 02330002
023400     CALL 'SUBPGM' USING WS-SUB-1, WS-SUB-2, WS-SUB-3             02340003
023500                   BY CONTENT WS1-TOT-MARK, WS1-TOT-PER           02350003
023600     IF (WS1-TOT-PER <= 45)                                       02360002
023700        MOVE 'D' TO MI001-GRADE                                   02370002
023800        MOVE 'POOR' TO MI001-LEVEL                                02380002
023900     END-IF                                                       02390004
024000     IF((WS1-TOT-PER > 45) AND (WS1-TOT-PER <= 65))               02400002
024100        MOVE 'C' TO MI001-GRADE                                   02410002
024200        MOVE 'AVERAGE' TO MI001-LEVEL                             02420002
024300     END-IF                                                       02430004
024400     IF((WS1-TOT-PER > 65) AND (WS1-TOT-PER <= 85))               02440002
024500        MOVE 'B' TO MI001-GRADE                                   02450002
024600        MOVE 'GOOD' TO MI001-LEVEL                                02460002
024700     END-IF                                                       02470004
024800     IF(WS1-TOT-PER > 85)                                         02480002
024900        MOVE 'A' TO MI001-GRADE                                   02490002
025000        MOVE 'EXCELLENT' TO MI001-LEVEL                           02500002
025100     END-IF                                                       02510004
025200     IF(MI001-GRADE = 'A' AND WS1-TOT-PER > 90)                   02520002
025300        MOVE 'Y' TO MI001-SCH-ELIG                                02530002
025400     ELSE                                                         02540002
025500        MOVE 'N' TO MI001-SCH-ELIG                                02550002
025600     END-IF                                                       02560002
025700     MOVE WS1-TOT-MARK TO MI001-TOT-MARK                          02570002
025800     MOVE WS1-TOT-PER TO MI001-TOT-PER                            02580002
025900     MOVE TI001-STUDENT-NO TO MI001-STUDENT-NO, WMI001-STUDENT-NO 02590010
026000     MOVE TI001-STUDENT-GEN TO MI001-STUDENT-GEN                  02600002
026100     MOVE TI001-SUB-1 TO MI001-SUB-1                              02610002
026200     MOVE TI001-SUB-2 TO MI001-SUB-2                              02620002
026300     MOVE TI001-SUB-3 TO MI001-SUB-3                              02630002
026400     WRITE MI001-OUT-RECORD FROM WMI001-OUT-RECORD                02640010
026500******************************************************************02650002
026600*ARRAR TO EXCEL FILE                                              02660002
026700*******************************************                       02670002
026800     SET WS-INX TO 1                                              02680002
026900     MOVE MI001-STUDENT-NO TO WS-STUDENT-NO(WS-INX)               02690002
027000     MOVE MI001-STUDENT-GEN TO WS-STUDENT-GEN(WS-INX)             02700002
027100     MOVE MI001-TOT-MARK TO WS-TOT-MARK(WS-INX)                   02710002
027200     MOVE MI001-TOT-PER TO WS-TOT-PER(WS-INX)                     02720002
027300     MOVE MI001-LEVEL TO WS-LEVEL(WS-INX)                         02730002
027400     IF(MI001-LEVEL = 'EXCELLENT')                                02740002
027500       MOVE WS-STUDENT-NO(WS-INX) TO MI003-STUDENT-NO,            02750011
027600                                      WMI003-STUDENT-NO           02760011
027700       MOVE WS-STUDENT-GEN(WS-INX) TO MI003-STUDENT-GEN           02770002
027800       MOVE WS-TOT-MARK(WS-INX) TO MI003-TOT-MARK                 02780002
027900       MOVE WS-TOT-PER(WS-INX) TO MI003-TOT-PER                   02790002
028000       MOVE WS-LEVEL(WS-INX) TO MI003-LEVEL                       02800002
028100       WRITE MI003-EXL-RECORD FROM WMI003-EXL-RECORD              02810011
028200     END-IF                                                       02820002
028300     SET WS-INX UP BY 1.                                          02830002
028400 2200-CORRECT-PARA-EXIT.                                          02840002
028500     EXIT.                                                        02850002
028600 2300-ERROR-FILE-PARA.                                            02860002
028700     DISPLAY '2300-ERROR-FILE-PARA'                               02870007
028800     IF(TI001-STUDENT-GEN IS NOT GREATER THAN SPACES)             02880003
028900       MOVE 'STUDENT-GEN' TO MI002-ERR-FIELD                      02890002
029000     END-IF                                                       02900002
029100     IF((TI001-SUB-1(1:2) IS NOT NUMERIC) OR                      02910008
029200                         (TI001-SUB-1(4:2) IS NOT NUMERIC))       02920008
029300       MOVE 'SUB-1' TO MI002-ERR-FIELD                            02930002
029400     END-IF                                                       02940002
029500     IF((TI001-SUB-2(1:2) IS NOT NUMERIC) OR                      02950008
029600                          (TI001-SUB-2(4:2) IS NOT NUMERIC))      02960008
029700       MOVE 'SUB-2' TO MI002-ERR-FIELD                            02970002
029800     END-IF                                                       02980002
029900     IF((TI001-SUB-3(1:2) IS NOT NUMERIC) OR                      02990008
030000                          (TI001-SUB-3(4:2) IS NOT NUMERIC))      03000008
030100       MOVE 'SUB-3' TO MI002-ERR-FIELD                            03010002
030200     END-IF                                                       03020002
030300     MOVE TI001-STUDENT-NO TO MI002-STUDENT-NO                    03030008
030400     MOVE TI001-STUDENT-GEN TO MI002-STUDENT-GEN                  03040008
030500     MOVE TI001-SUB-1 TO MI002-SUB-1                              03050002
030600     MOVE TI001-SUB-2 TO MI002-SUB-2                              03060002
030700     MOVE TI001-SUB-3 TO MI002-SUB-3                              03070002
030800       WRITE MI002-ERR-RECORD FROM WS-HEADER.                     03080013
030900 2300-ERROR-FILE-PARA-EXIT.                                       03090002
031000      EXIT.                                                       03100002
031100 3000-CLOSE-PARA.                                                 03110002
031200      CLOSE TI001-INP.                                            03120003
031300      EVALUATE TRUE                                               03130002
031400      WHEN WFS1-SUCCESS                                           03140002
031500         DISPLAY 'CLOSE SUCCESSFULLY'                             03150002
031600      WHEN OTHER                                                  03160002
031700         DISPLAY ' IO ERROR ' WS-FILE-STATUS1                     03170002
031800      PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  03180002
031900      END-EVALUATE.                                               03190002
032000      CLOSE MI001-OUT.                                            03200002
032100      EVALUATE TRUE                                               03210002
032200      WHEN WFS2-SUCCESS                                           03220002
032300         DISPLAY 'ESDS CLOSE SUCCESSFULLY'                        03230002
032400      WHEN OTHER                                                  03240002
032500         DISPLAY ' IO ERROR ' WS-FILE-STATUS2                     03250002
032600      PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  03260002
032700      END-EVALUATE.                                               03270002
032800      CLOSE MI002-ERR.                                            03280002
032900      EVALUATE TRUE                                               03290002
033000      WHEN WFS3-SUCCESS                                           03300002
033100         DISPLAY 'ERRORFILE CLOSE SUCCESSFULLY'                   03310002
033200      WHEN OTHER                                                  03320002
033300         DISPLAY ' IO ERROR ' WS-FILE-STATUS3                     03330002
033400      PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  03340002
033500      END-EVALUATE.                                               03350002
033600      CLOSE MI003-EXL.                                            03360002
033700      EVALUATE TRUE                                               03370002
033800      WHEN WFS4-SUCCESS                                           03380002
033900         DISPLAY 'EXECL CLOSE SUCCESSFULLY'                       03390002
034000      WHEN OTHER                                                  03400002
034100         DISPLAY ' IO ERROR ' WS-FILE-STATUS4                     03410002
034200      PERFORM 9000-TERMINATE-PARA THRU 9000-EXIT                  03420002
034300      END-EVALUATE.                                               03430002
034400 3000-EXIT-PARA.                                                  03440002
034500      EXIT.                                                       03450002
034600 9000-TERMINATE-PARA.                                             03460002
034700 9000-EXIT.                                                       03470002
034800      EXIT.                                                       03480002



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
