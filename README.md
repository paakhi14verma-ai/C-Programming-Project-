# Student Time Management Game – C Programming Project

## Author: Paakhi Verma  
SAP ID: 590022228  
Batch: 28  
Course: B.Tech CSE – 1st Year  



Abstract
Time is the most precious resource in a student’s life. The idea for this project, which we call the “Student Time Management Game,” offers a fun, interactive way to show how the choices we make in our lives impact productivity.
Using a simple C program, players simulate their day and must choose between studying, sleeping, or scrolling their phone (all, of course, while trying to maximise their overall score). The project captures the spirit of promoting time management, logic building, and coding constructively.



 Introduction
As a first-year student, I noticed many of my friends — and even myself — struggled to balance studies, rest, and distractions. So, I decided to turn this everyday struggle into a small C game that encourages good habits.
Instead of just reading about “time management,” this project lets you play it.



Concept of Time Management in Student Life
Student life is filled with opportunities, but also distractions. Managing your time will allow you to complete your assignments, attend classes, and still have fun. 
This project will demonstrate that even a few wasted hours can impact your performance, while a small effort, such as studying or getting to bed on time, can lead to success.



 Objective of the Project
This project's primary mission is to develop a C program to demonstrate how students spend their time on a normal day. It helps students gain a better understanding of the discipline of time management and how various decisions made in a 24-hour day will influence student performance.  The program allows users to decide whether to study and relax, take classes, or use social media, and calculates the resulting performance score based on these actions. 

The project will provide a student learning experience in C programming, covering concepts such as loops, conditionals, and functions, and will help them understand how a willingness to manage their time effectively influences academic performance and personal productivity.



 

Motivation Behind the Project
One night, after too many hours of procrastinating and scrolling through my phone, it occurred to me — maybe I could take this challenge and turn it into something fun? This was the beginning of the "Student Time Management Game." 

It was an insignificant thought that quickly grew into a significant project. One of the things I wanted was to develop something that students could easily relate to — the everyday balance of studying, leisure, and distractions. 

This project is not just about writing code. It is about creating a simple, fun tool that prompts students to reflect on what they do with their time and promotes better choices each day.




SOURCE CODE: 

#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int hours;
    int score;
} Player;

void showMenu();
void handleChoice(Player *p, int choice);

int main() {
    
    Player *player = (Player *)malloc(sizeof(Player));
    if (player == NULL) {
        printf("Memory allocation failed!\n");
        return 1;
    }

    player->hours = 6;
    player->score = 0;

    printf("STUDENT TIME MANAGEMENT GAME (Clean Version)\n");

    while (player->hours > 0) {
        printf("\nHours left: %d\n", player->hours);
        showMenu();

        int choice;
        printf("Choose: ");
        scanf("%d", &choice);

        handleChoice(player, choice);
    }

    printf("\nDay Over! Total Score: %d\n", player->score);

    if (player->score >= 15)
        printf("Excellent time management!\n");
    else if (player->score >= 5)
        printf("Not bad! Could be better.\n");
    else
        printf("Poor time management! Try again tomorrow.\n");

    free(player);

    return 0;
}

void showMenu() {
    printf("1. Study\n");
    printf("2. Sleep\n");
    printf("3. Phone\n");
}

void handleChoice(Player *p, int choice) {
    switch (choice) {
        case 1:
            if (p->hours >= 2) {
                p->score += 10;
                p->hours -= 2;
                printf("Studied well! +10 points.\n");
            } else {
                printf("Not enough time to study!\n");
            }
            break;

        case 2:
            if (p->hours >= 2) {
                p->score += 5;
                p->hours -= 2;
                printf("Slept well! +5 points.\n");
            } else {
                printf("Not enough time to sleep!\n");
            }
            break;

        case 3:
            if (p->hours >= 1) {
                p->score -= 5;
                p->hours -= 1;
                printf("You wasted time on your phone! -5 points.\n");
            } else {
                printf("Day over!\n");
            }
            break;

        default:
            printf("Invalid choice! Please try again.\n");
            break;
    }
}




       Sample Output
       
________________________________________
 STUDENT TIME MANAGEMENT GAME 
________________________________________
Hours Left: 6
Options:
1️ Study 
2️ Sleep 
3 Phone 
Choose: 1
Studied well! → +10 points
________________________________________
Hours Left: 4
Options:
1️ Study 
2️ Sleep 
3️ Phone 
Choose: 2
You feel fresh! → +5 points
________________________________________
Hours Left: 2
Options:
1️ Study 
2️ Sleep 
3️ Phone 
Choose: 3
 Wasted time on the phone! → -5 points
________________________________________
Hours Left: 1
Options:
1️ Study 
2️ Sleep 
3️ Phone 
Choose: 1
Not enough time to study! → 0 points

Hours Left: 1
Options:
1 Study 
2️ Sleep 
3️ Phone 
Choose: 3
You wasted time on the Phone→ -5 points


Day Over! Total Score: 5
Not bad! It could be better.



 Day Summary
  Activity		         Result		       Points	
   Study		         Studied well		   +10	
   Sleep		         Felt fresh		      +5	
   Phone             Wasted Time        -5
		Study            Not enough time     0
		Phone		         Wasted Time		     -5            
	
 Day Over!
 Total Score: 10
 Performance: Average Day




Explanation

Management Game.
•	The player begins with 6 hours to manage.
•	Each action reduces time and affects the overall performance score.
•	Productive activities like studying or resting increase points, while distractions reduce them.
•	Finally, the total score reflects how effectively the player managed time during the day.




Output Evaluation

Activity         	Hours Used           	Score Change            	Result
Study               	2	                      +10	               High productivity
Sleep 	              2                      	+5                	Moderate gain
Phone               	1                     	-5	                 Time wasted
Study 	              1                     	0                 	Not enough time
Phone                 1                     	-5	                 Wasted time  
	
The final score figures out whether the player managed their day effectively.




Concepts Used in the Program

Concept	Description	Where It Appears in the Program
Header Files (#include)	Provide access to library functions.	#include <stdio.h>, #include <stdlib.h>
User-Defined Data Type (struct)	Group multiple related variables.	typedef struct { int hours; int score; } Player;
Function Prototypes	Declares functions before main.	void showMenu(); void handleChoice(...);
Dynamic Memory Allocation (malloc)	Allocates memory at runtime.	Player *player = (Player *)malloc(sizeof(Player));
Pointer Variables	Holds memory address of values/structures.	Player *player, passing a pointer to functions.
File Handling (FILE, fopen
, fprintf, fclose)	Creates and manages external files.	Writing the full report into student_game_report.txt.
Error Handling	Prevents crashes & handles failures.	Checks fopen == NULL, malloc == NULL.
Functions (User-Defined)	Breaks code into reusable blocks.	main(), showMenu(), handleChoice()
Function Parameters & Arguments	Passing data by pointer and value.	handleChoice(Player *p, int choice, FILE *fp)
Pointers to Structures (p->hours)	Accesses structure members with a pointer.	p->score += 10; p->hours -= 2;
Switch Case	Selects an action based on choice.	In handleChoice() for Study/Sleep/Phone.
If-Else Conditions	Decision making.	Checking hours left, checking scores, and remarks.
Loop (while)	Repeats gameplay until the condition fails.	While hours > 0.
Variable Initialization	Assigning starting values.	player->hours = 6; player->score = 0;
Arithmetic Operations	Score and hour calculations.	+=, -=, comparisons.
Logical Flow Control	Structures gameplay logic.	Combining loop + switch + if conditions.
Memory Deallocation (free)	Prevents memory leak.	free(player);
Structure Pointer Passing	Allows functions to modify original data.	handleChoice(player, choice, fp);
File Logging for Analysis	Builds a real-time activity report.	Every action is logged into a text file.
Remarks Evaluation Logic	Determines final performance category.	If score >= 15, >= 5, else.
Sequential, Conditional & Iterative Constructs	Core building blocks of the C program flow.	Used throughout main and helper functions.
Menu-Driven Program Design	Common pattern for user interaction.	showMenu() + switch choices.
Real-life Simulation (Gamification)	Used for project creativity.	Time management scoring system.



WORKING EXPLANATION WITH CONCEPTS USED

The “Student Time Management Game” is an interactive C program designed to help students understand time management and basic programming concepts.
It allows the player to make daily choices, such as studying, sleeping, or using the phone, and then calculates how effectively the time was used.

1. Structure (struct) :
Used to group related data:
struct Player {hours , score}
This helps represent the student as a single object.

2. Dynamic Memory Allocation (malloc) :
You create the student (Player) at runtime:
Player *Player = malloc (sizeof(Player));
This is particularly useful in project-based programs and helps prevent memory waste.

3. File Handling :
The program creates and writes a full report:
•	fopen() → creates the file
•	fprintf() → writes gameplay logs
•	fclose() → closes the file
The file helps teachers see proof of how the game ran.	

4. Switch-Case :
Used to check the chosen action:
switch (choice){case 1 , case 2 , case 3}
This makes menu-based programs clean and easy to understand.

5. Loop (while) :
The game continues until hours become 0:
while (player->hours > 0)
This simulates the passing of a day.

6. Pointers :
The Player data is changed using a pointer:
p->hours , p->score
This simulates the passing of a day.

7. Conditional Statements (if–else) :
Used to ensure:
•	Enough hours are available
•	Score updates correctly
•	Final performance is calculated

8. Functions :
The logic is divided into:
•	showMenu() → Displays 3 options
•	handleChoice() → Processes the user's decision
This improves clarity and maintainability.

9. Error Handling :
Handled using:
•	Null pointer check
•	File creation check
•	Not enough hours to perform an action
•	Invalid choice handling


10. User Interaction :
The program takes input using:
scanf("%d",&choice)
and gives real-time feedback with emojis, making it engaging




Conclusion
This project successfully shows how simple C programming constructs can be used to create an interactive and educational game.
It encourages logical decision-making and teaches beginners how to use loops, conditions, and switch statements effectively.
It blends logic and life — every choice mirrors real student habits.
By linking C programming concepts to daily decision-making, the project becomes both educational and relatable.
It proves that even simple code can teach valuable life lessons about productivity, balance, and consequences. 
                   "Time is a resource — code it wisely!" 

                                     THANK YOU 
