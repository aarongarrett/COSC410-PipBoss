

# Pip Boss
This repository has been set up to get you started in completing your capstone project.

## Contents
  * [Project Overview](#project-overview)
    + [Prioritized Features](#prioritized-features)
    + [Grading Scheme](#grading-scheme)
  * [Project Details](#project-details)
    + [Definition of Done](#definition-of-done)
    + [Prioritized Features](#prioritized-features-1)
  * [Technical Details](#technical-details)
    + [Prerequisites](#prerequisites)
    + [Building the Project](#building-the-project)
    + [Directory Structure](#directory-structure)
    + [IDE Setup](#ide-setup)
      - [Intellij](#intellij)
      - [Eclipse](#eclipse)
  * [Example Output](#example-output)


## Project Overview
-------------------
In this project, you will be creating a program that allows users to play a digital version of [Las Vegas Royale](https://boardgamegeek.com/boardgame/271319/las-vegas-royale).


### Prioritized Features
The core features for this project are broken into phases, where Phase 0 is of higher priority than Phase 1, etc. Feature 1 corresponds to Phase 0, and so forth.


### Grading Scheme
This project is worth 50 points (50% of the total grade for the course). These points are awarded in two ways. First, each of the 4 sprints end in a sprint review, at which point your team's work is evaluated. Each sprint is worth a maximum of 10 points for each member of the team. (Except in highly unusual circumstances, all members receive the same grade for a sprint.) Second, the final 10 points are determined according to how many features you complete by the project's final deadline. That scale is as follows, determined by the **final feature** that your team completes:

| Phase   | Points |
|---------|--------|
| 0       | 0      |
| 1       | 0      |
| 2       | 0      |
| 3       | 0      |
| 4       | 0      |
| 5       | 1      |
| 6       | 2      |
| 7       | 3      |
| 8       | 4      |
| 9       | 6      |
| 10      | 8      |
| 11      | 10     |
| 12      | 12     |
| 13      | 15     |

Note that it is possible to receive more than 10 points for this component, with any additional points counting as "bonus" toward the final course grade.


## Project Details
------------------

### Definition of Done
The *definition of done* for **any** feature is that it passes all automated acceptance tests, has a codebase that achieves at least 85% branch coverage from its unit tests, has complete API documentation, and has a fully documented user guide.

### Console Output
The console version of the game should always provide standardized, specific output as the game progresses. See the [example output](#example-output). In any cases where the dice must be specified, the format should be "[A, B, C]" where A, B, C, etc., where those values are digits 1-6. In the event that a large die is used, its value should be listed as "A+A" (e.g., 4+4) to denote that it represents 2 dice. In any cases where a player is specified, the format should be "PX" (e.g., P1, P2, etc.). Dollar amounts are given in units of 10,000 (e.g., $30,000 in the board game would correspond to $3 in this implementation). Finally, any singular/plural units should be output accordingly (e.g., chip/chips, die/dice, etc.).

* Lifecycle Updates - The user should be notified at each stage of the game as follows:
    * Game Start: "The game has started. It will consist of X round(s) and have Y player(s). Each player has M regular die(ce) and N large die(ce) with C chip(s) per round."
    * Round Start: "Round X has started."
    * Round End: "Round X has ended."
    * Payout End: "Round X payout has ended."
    * Game End: "The game is over. The final game state is below." (followed by the game state)
* Player Actions - The user should be notified of player actions as follows:
    * Dice Rolled: "PX rolled [DICE]." (where DICE is described above)
    * Dice Placed: "PX placed [DICE]." (where DICE is described above)
    * Chip Used: "PX used a chip and has Y chip(s) left."
    * Chips Added: "PX gained Y chip(s): REASON"
    * Chips Lost: "PX lost Y chip(s): REASON"
    * Money Added: "PX gained $Y: REASON"
    * Money Lost: "PX lost $Y: REASON"
* Casino Updates - The user should be notified of changes to casinos as follows:
    * Dice Added: "Casino X gained [DICE] from PY."
    * Dice Removed: "Casino X lost [DICE] from PY."
    * Minigame Added: "Casino X added the minigame NAME."
    * Minigame Updated: "The minigame NAME at Casino X has the following update: UPDATE"

The game state should have **exactly** the following format (using values for the example):
```
----------------------------      PLAYERS      ----------------------------
 player : money  dice  DICE  chips                                         
     P1 :     3     0     1      4
     P2 :     3     0     0      2
     P3 :     4     1     0      2

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   5   3 :  $$2                                                        
 Pay Day - Gain $1 for each casino where you have presence.                
 [2]   6   3 :       $$1                                                   
 Black Box - During payout, winner plays split/choose for winnings. 
 [3]   6   3 :    3    3  $$2                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [4]   7   3 :  $$2                                                        
 [5]   8   5 :       $$5  $ 1                                              
 [6]   8   6 :            $$5                                              
```

The player information should specify the number of remaining regular dice ("dice") and large dice ("DICE"). The casino information should specify the casino number ("#"), the large payout ("$$"), the small payout ("$"), and the number of dice belonging to each player ("P1", etc.). The current winner of the large payout should have "$$" before their allocated dice number. Likewise, the current winner of the small payout should have "$" before their allocated dice number. Any minigame at a casino should list its name and summary below the casino's row. Any line in the output has a maximum width of 75 characters and should be broken at whitespace if the line exceeds that amount.


### Prioritized Features

#### Phase 0
The user should be able to play a console version of the game that lasts only a single round, has only a single player, and that player has only 7 standard dice and no chips.  

#### Phase 1
Same as Phase 0 but now the player gains 2 chips at the start of the round.

#### Phase 2
Same as Phase 1 but now the player has 1 large die as well as the 7 regular dice.

#### Phase 3
Same as Phase 2 but now the player has 2 AI opponents that play aggressively, where they always place the most dice possible each turn.

#### Phase 4
Same as Phase 3 but with 3 rounds instead of only 1 (with chips allocated accordingly each round).

#### Phase 5
Same as Phase 4, but now the minigame Jackpot should be added to Casino 1. 

#### Phase 6
Same as Phase 5, but now the minigame Pay Day should be added (randomly assigning it to Casino 1 or 2 with Jackpot assigned to the other).

#### Phase 7
Same as Phase 6, but now the minigame Fifty Fifty should be added (randomly assigning the 3 minigames each to one of the lowest 3 casinos). The AI opponents play this game as follows:
* If the payout is $0, they roll.
* If the mark is between 5 and 8, inclusive, they stop and take the payout.
* If the mark is less than 5, they choose higher/more.
* If the mark is greater than 8, they choose lower/less.
The informative prompt for players should contain the following:
"Would you like to take the payout (0), roll less (1), or roll more (2)? (0, 1, 2): "

#### Phase 8
Same as Phase 7, but now the minigame Lucky Punch should be added (dropping Jackpot and randomly assigning the other 3 as before). The AI opponents should randomly choose an option in all cases.
The informative prompt for players should allow the choice to be 2 chips, $3, or $4, and it should include the following:
"What is your choice? (1, 2, or 3): "

#### Phase 9
Same as Phase 8, but now the minigame High Five should be added (dropping Pay Day and randomly assigning the other 3 as before).

#### Phase 10
Same as Phase 9, but now the minigame Black Box should be added (dropping Fifty Fifty and randomly assigning the other 3 as before). The AI opponents should take the larger split 75% of the time when they are the active player, and they should randomly assign to the 2 groups if they are not the active player. The informative prompt for players should contain the following for choosing piles to take:
"Which pile would you like? (1 or 2): "
It should also contain the following for choosing which pile to place an option:
"In which pile would you like to place X? (1 or 2)" where X is the value to assign.

#### Phase 11
Same as Phase 10, but now the minigame Block It should be added (dropping Lucky Punch and randomly assigning the other 3 as before). The AI opponents should randomly choose a group of blocking dice and assign them to a randomly chosen casino. The informative prompt for players should contain the following:
"The dice pool options are [X]." where X is a comma-separated list of dice counts in each pool. It should also contain the prompts "Which pool would you like?" and "Which casino will you add them to?".

#### Phase 12
Same as Phase 11, but now the minigame Bad Luck should be added (dropping High Five and randomly assigning the other 3 as before).

#### Phase 13
Add a graphical user interface to allow playing the game as in Phase 12.




## Technical Details
--------------------
### Prerequisites
This project assumes that you have already [installed Java 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) on your system. 

### Building the Project
After you have cloned the repository, you should be able to navigate to the root directory containing the **gradle.build** file. There, you can build the project by running the command

`gradlew build`

Then, you can run the unit test coverage report.

`gradlew jacocoTestReport`

Then, you can run the acceptance tests. 

`gradlew cucumber`

You can even do multiple things in one statement:

`gradlew build jacocoTestReport cucumber`

When you want to get rid of all of the temporary files (like compiled class files and such), you can say

`gradlew clean`

If you want to do a full build and reporting from a clean project, you can just string it all together:

`gradlew clean build jacocoTestReport cucumber`

If you want to create the generated documentation (based on your Javadoc comments), you can say

`gradlew javadoc`

If you want to run the application, you can say

`java -jar app/build/libs/PipBoss.jar <phaseNumber>`


## Example Output
-----------------
```
The game has started. It will consist of 3 rounds and has 3 players.       
Each player has 7 regular and 1 large dice with 2 chips per round.         
Casino 1 added the minigame Pay Day.                                       
Casino 2 added the minigame High Five.                                     
Casino 3 added the minigame Fifty Fifty.                                   
Casino 4 added the minigame Lucky Punch.                                   
Casino 5 added the minigame Black Box.                                     
Casino 6 added the minigame Jackpot.                                       
P1 gained 2 chips: Chips for Round 1.                                      
P2 gained 2 chips: Chips for Round 1.                                      
P3 gained 2 chips: Chips for Round 1.                                      
Round 1 has started.                                                       
----------------------------      PLAYERS      ----------------------------
 player : money  dice  DICE  chips                                         
     P1 :     0     7     1      2
     P2 :     0     7     1      2
     P3 :     0     7     1      2

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :                                                             
 Pay Day - Gain $1 for each casino where you have presence.                
 [2]   7   5 :                                                             
 High Five - The first player to place at least 5 dice here wins $10.      
 [3]   8   4 :                                                             
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [4]  10   5 :                                                             
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [5]   8   8 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        
 [6]  10   9 :                                                             
 Jackpot - Roll doubles or 7 to win $3.                                    

P1 placed [4, 4+4].                                                        
Casino 4 gained [4,4+4] from P1.                                           
P1 gained $3: Lucky Punch (chose $3 and P2 guessed 2 chips).               
The minigame Lucky Punch at Casino 4 has the following update: P1 chose $3 
and P2 guessed 2 chips.                                                    
P2 rolled [5, 4, 2, 2, 6, 1, 2, 3+3].                                      
P2 placed [2, 2, 2].                                                       
Casino 2 gained [2,2,2] from P2.                                           
P3 rolled [3, 3, 3, 6, 6, 6, 2, 3+3].                                      
P3 placed [3, 3, 3, 3+3].                                                  
Casino 3 gained [3,3,3,3+3] from P3.                                       
The minigame Fifty Fifty at Casino 3 has the following update: P3's choice 
was less. The old mark was 7 and the new mark is 6. The payout is 1 chip.  
The minigame Fifty Fifty at Casino 3 has the following update: P3's choice 
was stop. The payout is 1 chip.                                            
P3 gained 1 chip: Fifty Fifty.                                             
----------------------------      PLAYERS      ----------------------------
 player : money  dice  DICE  chips                                         
     P1 :     3     6     0      2
     P2 :     0     4     1      2
     P3 :     0     4     0      3

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :                                                             
 Pay Day - Gain $1 for each casino where you have presence.                
 [2]   7   5 :       $$3                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [3]   8   4 :            $$5                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [4]  10   5 :  $$3                                                        
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [5]   8   8 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        
 [6]  10   9 :                                                             
 Jackpot - Roll doubles or 7 to win $3.                                    

P1 placed [2, 2, 2].                                                       
Casino 2 gained [2,2,2] from P1.                                           
P2 rolled [6, 4, 4, 1, 1+1].                                               
P2 placed [1, 1+1].                                                        
Casino 1 gained [1,1+1] from P2.                                           
P2 gained 2 chips: Pay Day (has presence at 2 casinos).                    
The minigame Pay Day at Casino 1 has the following update: P2 has presence 
at 2 casinos.                                                              
P3 rolled [4, 4, 4, 3].                                                    
P3 placed [4, 4, 4].                                                       
Casino 4 gained [4,4,4] from P3.                                           
The minigame Lucky Punch at Casino 4 has the following update: P3 chose $3 
and P1 guessed $3.                                                         
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :     3     3      2
     P2 :     0     3      4
     P3 :     0     1      3

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3                                                   
 Pay Day - Gain $1 for each casino where you have presence.                
 [2]   7   5 :    3    3                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [3]   8   4 :            $$5                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [4]  10   5 :    3         3                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [5]   8   8 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        
 [6]  10   9 :                                                             
 Jackpot - Roll doubles or 7 to win $3.                                    

P1 placed [6, 6].                                                          
Casino 6 gained [6,6] from P1.                                             
The minigame Jackpot at Casino 6 has the following update: [1, 2] was      
rolled. Potential payout is now $4.                                        
P2 rolled [4, 6, 4].                                                       
P2 placed [4, 4].                                                          
Casino 4 gained [4,4] from P2.                                             
P2 gained $3: Lucky Punch (chose $3 and P3 guessed 2 chips).               
The minigame Lucky Punch at Casino 4 has the following update: P2 chose $3 
and P3 guessed 2 chips.                                                    
P3 rolled [4].                                                             
P3 placed [4].                                                             
Casino 4 gained [4] from P3.                                               
P3 gained $4: Lucky Punch (chose $4 and P1 guessed $3).                    
The minigame Lucky Punch at Casino 4 has the following update: P3 chose $4 
and P1 guessed $3.                                                         
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :     3     1      2
     P2 :     3     1      4
     P3 :     4     0      3

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3                                                   
 Pay Day - Gain $1 for each casino where you have presence.                
 [2]   7   5 :    3    3                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [3]   8   4 :            $$5                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [4]  10   5 :  $ 3    2  $$4                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [5]   8   8 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        
 [6]  10   9 :  $$2                                                        
 Jackpot - Roll doubles or 7 to win $4.                                    

P1 placed [3].                                                             
Casino 3 gained [3] from P1.                                               
The minigame Fifty Fifty at Casino 3 has the following update: P1's choice 
was more. The old mark was 5 and the new mark is 7. The payout is 1 chip.  
The minigame Fifty Fifty at Casino 3 has the following update: P1's choice 
was stop. The payout is 1 chip.                                            
P1 gained 1 chip: Fifty Fifty.                                             
P2 rolled [2].                                                             
P2 placed [2].                                                             
Casino 2 gained [2] from P2.                                               
Round 1 has ended.                                                         
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :     3     0      3
     P2 :     3     0      4
     P3 :     4     0      3

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3                                                   
 Pay Day - Gain $1 for each casino where you have presence.                
 [2]   7   5 :  $ 3  $$4                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [3]   8   4 :  $ 1       $$5                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [4]  10   5 :  $ 3    2  $$4                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [5]   8   8 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        
 [6]  10   9 :  $$2                                                        
 Jackpot - Roll doubles or 7 to win $4.                                    

P1 gained $10: Payout from Casino 6 for Round 1.                           
P3 gained $10: Payout from Casino 4 for Round 1.                           
P1 gained $5: Payout from Casino 4 for Round 1.                            
P3 gained $8: Payout from Casino 3 for Round 1.                            
P1 gained $4: Payout from Casino 3 for Round 1.                            
P2 gained $7: Payout from Casino 2 for Round 1.                            
P1 gained $5: Payout from Casino 2 for Round 1.                            
P2 gained $4: Payout from Casino 1 for Round 1.                            
Round 1 payout has ended.                                                  
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    27     0      3
     P2 :    14     0      4
     P3 :    22     0      3

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3                                                   
 Pay Day - Gain $1 for each casino where you have presence.                
 [2]   7   5 :  $ 3  $$4                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [3]   8   4 :  $ 1       $$5                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [4]  10   5 :  $ 3    2  $$4                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [5]   8   8 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        
 [6]  10   9 :  $$2                                                        
 Jackpot - Roll doubles or 7 to win $4.                                    

Casino 1 added the minigame Fifty Fifty.                                   
Casino 2 added the minigame Pay Day.                                       
Casino 3 added the minigame Lucky Punch.                                   
Casino 4 added the minigame Jackpot.                                       
Casino 5 added the minigame High Five.                                     
Casino 6 added the minigame Black Box.                                     
P1 gained 2 chips: Chips for Round 2.                                      
P2 gained 2 chips: Chips for Round 2.                                      
P3 gained 2 chips: Chips for Round 2.                                      
Round 2 has started.                                                       
----------------------------      PLAYERS      ----------------------------
 player : money  dice  DICE  chips                                         
     P1 :    27     7     1      5
     P2 :    14     7     1      6
     P3 :    22     7     1      5

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   3 :                                                             
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [2]   6   3 :                                                             
 Pay Day - Gain $1 for each casino where you have presence.                
 [3]   8   3 :                                                             
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [4]   7   7 :                                                             
 Jackpot - Roll doubles or 7 to win $3.                                    
 [5]   8   8 :                                                             
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   7 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        

P1 placed [2, 2, 2].                                                       
Casino 2 gained [2,2,2] from P1.                                           
P1 gained 1 chip: Pay Day (has presence at 1 casino).                      
The minigame Pay Day at Casino 2 has the following update: P1 has presence 
at 1 casino.                                                               
P2 rolled [5, 5, 6, 6, 2, 5, 4, 6+6].                                      
P2 placed [5, 5, 5].                                                       
Casino 5 gained [5,5,5] from P2.                                           
P3 rolled [3, 4, 4, 3, 4, 4, 4, 2+2].                                      
P3 placed [4, 4, 4, 4, 4].                                                 
Casino 4 gained [4,4,4,4,4] from P3.                                       
The minigame Jackpot at Casino 4 has the following update: [2, 4] was      
rolled. Potential payout is now $4.                                        
----------------------------      PLAYERS      ----------------------------
 player : money  dice  DICE  chips                                         
     P1 :    27     4     1      6
     P2 :    14     4     1      6
     P3 :    22     2     1      5

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   3 :                                                             
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [2]   6   3 :  $$3                                                        
 Pay Day - Gain $1 for each casino where you have presence.                
 [3]   8   3 :                                                             
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [4]   7   7 :            $$5                                              
 Jackpot - Roll doubles or 7 to win $4.                                    
 [5]   8   8 :       $$3                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   7 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        

P1 placed [1].                                                             
Casino 1 gained [1] from P1.                                               
The minigame Fifty Fifty at Casino 1 has the following update: P1's choice 
was more. The old mark was 3 and the new mark is 9. The payout is 1 chip.  
The minigame Fifty Fifty at Casino 1 has the following update: P1's choice 
was less. The old mark was 9 and the new mark is 6. The payout is $3.      
The minigame Fifty Fifty at Casino 1 has the following update: P1's choice 
was stop. The payout is $3.                                                
P1 gained $3: Fifty Fifty.                                                 
P2 rolled [2, 5, 4, 6, 4+4].                                               
P2 placed [4, 4+4].                                                        
Casino 4 gained [4,4+4] from P2.                                           
The minigame Jackpot at Casino 4 has the following update: [5, 4] was      
rolled. Potential payout is now $5.                                        
P3 rolled [1, 1, 6+6].                                                     
P3 placed [1, 1].                                                          
Casino 1 gained [1,1] from P3.                                             
The minigame Fifty Fifty at Casino 1 has the following update: P3's choice 
was less. The old mark was 10 and the new mark is 6. The payout is 1 chip. 
The minigame Fifty Fifty at Casino 1 has the following update: P3's choice 
was stop. The payout is 1 chip.                                            
P3 gained 1 chip: Fifty Fifty.                                             
----------------------------      PLAYERS      ----------------------------
 player : money  dice  DICE  chips                                         
     P1 :    30     3     1      6
     P2 :    14     3     0      6
     P3 :    22     0     1      6

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   3 :  $ 1       $$2                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [2]   6   3 :  $$3                                                        
 Pay Day - Gain $1 for each casino where you have presence.                
 [3]   8   3 :                                                             
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [4]   7   7 :       $ 3  $$5                                              
 Jackpot - Roll doubles or 7 to win $5.                                    
 [5]   8   8 :       $$3                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   7 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        

P1 placed [2+2].                                                           
Casino 2 gained [2+2] from P1.                                             
P1 gained 2 chips: Pay Day (has presence at 2 casinos).                    
The minigame Pay Day at Casino 2 has the following update: P1 has presence 
at 2 casinos.                                                              
P2 rolled [1, 2, 2].                                                       
P2 placed [2, 2].                                                          
Casino 2 gained [2,2] from P2.                                             
P2 gained $3: Pay Day (has presence at 3 casinos).                         
The minigame Pay Day at Casino 2 has the following update: P2 has presence 
at 3 casinos.                                                              
P3 rolled [1+1].                                                           
P3 placed [1+1].                                                           
Casino 1 gained [1+1] from P3.                                             
The minigame Fifty Fifty at Casino 1 has the following update: P3's choice 
was more. The old mark was 6 and the new mark is 3. The payout is $0.      
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    30     3      8
     P2 :    17     1      6
     P3 :    22     0      6

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   3 :  $ 1       $$4                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [2]   6   3 :  $$5  $ 2                                                   
 Pay Day - Gain $1 for each casino where you have presence.                
 [3]   8   3 :                                                             
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [4]   7   7 :       $ 3  $$5                                              
 Jackpot - Roll doubles or 7 to win $5.                                    
 [5]   8   8 :       $$3                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   7 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        

P1 placed [1, 1].                                                          
Casino 1 gained [1,1] from P1.                                             
The minigame Fifty Fifty at Casino 1 has the following update: P1's choice 
was less. The old mark was 12 and the new mark is 8. The payout is 1 chip. 
The minigame Fifty Fifty at Casino 1 has the following update: P1's choice 
was stop. The payout is 1 chip.                                            
P1 gained 1 chip: Fifty Fifty.                                             
P2 rolled [2].                                                             
P2 placed [2].                                                             
Casino 2 gained [2] from P2.                                               
P2 gained $3: Pay Day (has presence at 3 casinos).                         
The minigame Pay Day at Casino 2 has the following update: P2 has presence 
at 3 casinos.                                                              
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    30     1      9
     P2 :    20     0      6
     P3 :    22     0      6

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   3 :  $ 3       $$4                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [2]   6   3 :  $$5  $ 3                                                   
 Pay Day - Gain $1 for each casino where you have presence.                
 [3]   8   3 :                                                             
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [4]   7   7 :       $ 3  $$5                                              
 Jackpot - Roll doubles or 7 to win $5.                                    
 [5]   8   8 :       $$3                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   7 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        

P1 placed [5].                                                             
Casino 5 gained [5] from P1.                                               
Round 2 has ended.                                                         
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    30     0      9
     P2 :    20     0      6
     P3 :    22     0      6

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   3 :  $ 3       $$4                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [2]   6   3 :  $$5  $ 3                                                   
 Pay Day - Gain $1 for each casino where you have presence.                
 [3]   8   3 :                                                             
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [4]   7   7 :       $ 3  $$5                                              
 Jackpot - Roll doubles or 7 to win $5.                                    
 [5]   8   8 :  $ 1  $$3                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   7 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        

P2 gained $8: Payout from Casino 5 for Round 2.                            
P1 gained $8: Payout from Casino 5 for Round 2.                            
P3 gained $7: Payout from Casino 4 for Round 2.                            
P2 gained $7: Payout from Casino 4 for Round 2.                            
P1 gained $6: Payout from Casino 2 for Round 2.                            
P2 gained $3: Payout from Casino 2 for Round 2.                            
P3 gained $4: Payout from Casino 1 for Round 2.                            
P1 gained $3: Payout from Casino 1 for Round 2.                            
Round 2 payout has ended.                                                  
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    47     0      9
     P2 :    38     0      6
     P3 :    33     0      6

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   3 :  $ 3       $$4                                              
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [2]   6   3 :  $$5  $ 3                                                   
 Pay Day - Gain $1 for each casino where you have presence.                
 [3]   8   3 :                                                             
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [4]   7   7 :       $ 3  $$5                                              
 Jackpot - Roll doubles or 7 to win $5.                                    
 [5]   8   8 :  $ 1  $$3                                                   
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   7 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        

Casino 1 added the minigame Lucky Punch.                                   
Casino 2 added the minigame Black Box.                                     
Casino 3 added the minigame Jackpot.                                       
Casino 4 added the minigame Fifty Fifty.                                   
Casino 5 added the minigame High Five.                                     
Casino 6 added the minigame Pay Day.                                       
P1 gained 2 chips: Chips for Round 3.                                      
P2 gained 2 chips: Chips for Round 3.                                      
P3 gained 2 chips: Chips for Round 3.                                      
Round 3 has started.                                                       
P2 rolled [1, 6, 1, 2, 6, 2, 1, 3+3].                                      
P2 placed [1, 1, 1].                                                       
Casino 1 gained [1,1,1] from P2.                                           
The minigame Lucky Punch at Casino 1 has the following update: P2 chose 2  
chips and P3 guessed 2 chips.                                              
P3 rolled [2, 4, 2, 4, 6, 6, 6, 1+1].                                      
P3 placed [6, 6, 6].                                                       
Casino 6 gained [6,6,6] from P3.                                           
P3 gained 1 chip: Pay Day (has presence at 1 casino).                      
The minigame Pay Day at Casino 6 has the following update: P3 has presence 
at 1 casino.                                                               
----------------------------      PLAYERS      ----------------------------
 player : money  dice  DICE  chips                                         
     P1 :    47     7     1     11
     P2 :    38     4     1      8
     P3 :    33     4     1      9

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3                                                   
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [2]   5   5 :                                                             
 Black Box - During payout, winner plays split/choose for winnings.        
 [3]   6   6 :                                                             
 Jackpot - Roll doubles or 7 to win $3.                                    
 [4]  10   3 :                                                             
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [5]   9   5 :                                                             
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   5 :            $$3                                              
 Pay Day - Gain $1 for each casino where you have presence.                

P1 placed [2, 2, 2].                                                       
Casino 2 gained [2,2,2] from P1.                                           
P2 rolled [3, 2, 2, 3, 2+2].                                               
P2 placed [2, 2, 2+2].                                                     
Casino 2 gained [2,2,2+2] from P2.                                         
P3 rolled [3, 1, 1, 6, 3+3].                                               
P3 placed [1, 1].                                                          
Casino 1 gained [1,1] from P3.                                             
The minigame Lucky Punch at Casino 1 has the following update: P3 chose $4 
and P1 guessed $4.                                                         
----------------------------      PLAYERS      ----------------------------
 player : money  dice  DICE  chips                                         
     P1 :    47     4     1     11
     P2 :    38     2     0      8
     P3 :    33     2     1      9

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3  $ 2                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [2]   5   5 :  $ 3  $$4                                                   
 Black Box - During payout, winner plays split/choose for winnings.        
 [3]   6   6 :                                                             
 Jackpot - Roll doubles or 7 to win $3.                                    
 [4]  10   3 :                                                             
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [5]   9   5 :                                                             
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   5 :            $$3                                              
 Pay Day - Gain $1 for each casino where you have presence.                

P1 placed [3, 3+3].                                                        
Casino 3 gained [3,3+3] from P1.                                           
The minigame Jackpot at Casino 3 has the following update: [1, 3] was      
rolled. Potential payout is now $4.                                        
P2 rolled [5, 3].                                                          
P2 placed [3].                                                             
Casino 3 gained [3] from P2.                                               
P2 gained $4: Jackpot ([3, 3] -> $4).                                      
The minigame Jackpot at Casino 3 has the following update: [3][3] was      
rolled, and payout was $4. Potential payout is $3.                         
P3 rolled [3, 5, 3+3].                                                     
P3 placed [3, 3+3].                                                        
Casino 3 gained [3,3+3] from P3.                                           
The minigame Jackpot at Casino 3 has the following update: [5, 3] was      
rolled. Potential payout is now $4.                                        
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    47     3     11
     P2 :    42     1      8
     P3 :    33     1      9

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3  $ 2                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [2]   5   5 :  $ 3  $$4                                                   
 Black Box - During payout, winner plays split/choose for winnings.        
 [3]   6   6 :    3  $$1    3                                              
 Jackpot - Roll doubles or 7 to win $4.                                    
 [4]  10   3 :                                                             
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [5]   9   5 :                                                             
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   5 :            $$3                                              
 Pay Day - Gain $1 for each casino where you have presence.                

P1 placed [3].                                                             
Casino 3 gained [3] from P1.                                               
P1 gained $4: Jackpot ([1, 6] -> $4).                                      
The minigame Jackpot at Casino 3 has the following update: [1][6] was      
rolled, and payout was $4. Potential payout is $3.                         
P2 rolled [4].                                                             
P2 placed [4].                                                             
Casino 4 gained [4] from P2.                                               
The minigame Fifty Fifty at Casino 4 has the following update: P2's choice 
was less. The old mark was 10 and the new mark is 9. The payout is 1 chip. 
The minigame Fifty Fifty at Casino 4 has the following update: P2's choice 
was less. The old mark was 9 and the new mark is 10. The payout is $0.     
P3 rolled [5].                                                             
P3 placed [5].                                                             
Casino 5 gained [5] from P3.                                               
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    51     2     11
     P2 :    42     0      8
     P3 :    33     0      9

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3  $ 2                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [2]   5   5 :  $ 3  $$4                                                   
 Black Box - During payout, winner plays split/choose for winnings.        
 [3]   6   6 :  $$4    1  $ 3                                              
 Jackpot - Roll doubles or 7 to win $3.                                    
 [4]  10   3 :       $$1                                                   
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [5]   9   5 :            $$1                                              
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   5 :            $$3                                              
 Pay Day - Gain $1 for each casino where you have presence.                

P1 placed [3].                                                             
Casino 3 gained [3] from P1.                                               
The minigame Jackpot at Casino 3 has the following update: [3, 5] was      
rolled. Potential payout is now $4.                                        
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    51     1     11
     P2 :    42     0      8
     P3 :    33     0      9

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3  $ 2                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [2]   5   5 :  $ 3  $$4                                                   
 Black Box - During payout, winner plays split/choose for winnings.        
 [3]   6   6 :  $$5    1  $ 3                                              
 Jackpot - Roll doubles or 7 to win $4.                                    
 [4]  10   3 :       $$1                                                   
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [5]   9   5 :            $$1                                              
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   5 :            $$3                                              
 Pay Day - Gain $1 for each casino where you have presence.                

P1 placed [4].                                                             
Casino 4 gained [4] from P1.                                               
The minigame Fifty Fifty at Casino 4 has the following update: P1's choice 
was more. The old mark was 4 and the new mark is 9. The payout is 1 chip.  
The minigame Fifty Fifty at Casino 4 has the following update: P1's choice 
was less. The old mark was 9 and the new mark is 5. The payout is $3.      
The minigame Fifty Fifty at Casino 4 has the following update: P1's choice 
was stop. The payout is $3.                                                
P1 gained $3: Fifty Fifty.                                                 
Round 3 has ended.                                                         
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    54     0     11
     P2 :    42     0      8
     P3 :    33     0      9

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3  $ 2                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [2]   5   5 :  $ 3  $$4                                                   
 Black Box - During payout, winner plays split/choose for winnings.        
 [3]   6   6 :  $$5    1  $ 3                                              
 Jackpot - Roll doubles or 7 to win $4.                                    
 [4]  10   3 :    1    1                                                   
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [5]   9   5 :            $$1                                              
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   5 :            $$3                                              
 Pay Day - Gain $1 for each casino where you have presence.                

P2 gained $10: Black Box (chose 00226 out of 00226|0).                     
The minigame Black Box at Casino 2 has the following update: P3 split as   
00226|0 and P2 chose 00226.                                                
P3 gained $10: Payout from Casino 6 for Round 3.                           
P3 gained $9: Payout from Casino 5 for Round 3.                            
P1 gained $6: Payout from Casino 3 for Round 3.                            
P3 gained $6: Payout from Casino 3 for Round 3.                            
P2 gained $5: Payout from Casino 2 for Round 3.                            
P1 gained $5: Payout from Casino 2 for Round 3.                            
P2 gained $4: Payout from Casino 1 for Round 3.                            
P3 gained $4: Payout from Casino 1 for Round 3.                            
Round 3 payout has ended.                                                  
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    65     0     11
     P2 :    61     0      8
     P3 :    62     0      9

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3  $ 2                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [2]   5   5 :  $ 3  $$4                                                   
 Black Box - During payout, winner plays split/choose for winnings.        
 [3]   6   6 :  $$5    1  $ 3                                              
 Jackpot - Roll doubles or 7 to win $4.                                    
 [4]  10   3 :    1    1                                                   
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [5]   9   5 :            $$1                                              
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   5 :            $$3                                              
 Pay Day - Gain $1 for each casino where you have presence.                

The game is over. The final game state is below.                           
----------------------------      PLAYERS      ----------------------------
 player : money  dice  chips                                               
     P1 :    65     0     11
     P2 :    61     0      8
     P3 :    62     0      9

----------------------------      CASINOS      ----------------------------
  #   $$   $     P1   P2   P3                                              
 [1]   4   4 :       $$3  $ 2                                              
 Lucky Punch - Choose 1, 2, or 3 to win 2 chips, $3, or $4.                
 [2]   5   5 :  $ 3  $$4                                                   
 Black Box - During payout, winner plays split/choose for winnings.        
 [3]   6   6 :  $$5    1  $ 3                                              
 Jackpot - Roll doubles or 7 to win $4.                                    
 [4]  10   3 :    1    1                                                   
 Fifty Fifty - Keep rolling versus target or stop and take payout.         
 [5]   9   5 :            $$1                                              
 High Five - The first player to place at least 5 dice here wins $10.      
 [6]  10   5 :            $$3                                              
 Pay Day - Gain $1 for each casino where you have presence.                

The final scores are as follows: 
P1: $76
P2: $69
P3: $71
```
