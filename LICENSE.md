
 //Magic Number Game - A Program in C

#include <stdio.h>
#include <graphics.h>
#include <dos.h>
#include <string.h>

void InitGraphicMode();
void Welcome();
void StartGame();
void DisplayName(int );
void Clear();

void main()
{
		 InitGraphicMode();
		 Welcome();
		 getch();
		 StartGame();
		 closegraph();
}
void InitGraphicMode()
{
   int gdriver = DETECT, gmode, errorcode;
   //In next line the path of bgi files  is taken
   initgraph(&gdriver, &gmode, "c:\\T URBOC3\\bgi");
   errorcode = graphresult();
   if (errorcode != grOk)  /* an error occurred */
   {
		    printf("Graphics error: %s", grapherrormsg(errorcode));
		    printf("Press any key to halt:");
		    getch();
		    exit(1);             /* return with error code */
		 }
}
//to print the welcome screen
void Welcome()
{
		 char pattern[8] = {0x00, 0x70, 0x20, 0x27, 0x00, 0x27, 0x20, 0x70};
		 int i;

		 setfillpattern(pattern, BLUE);
		 for(i=0;i<=320;i++)
		 {
				 bar(320-i,240-i*0.75,320+i,240+i*0.75);
				 delay ( 1 ) ;
		 }
		 settextjustify(1,1);
		 DisplayName(100);
		 settextstyle(5,0,4);
		 music();
		 delay(3);
}
//to Start the game
void StartGame()
{
		 void FirstScreen();
		 char ShowList1(),ShowList2(),ShowList3(),ShowList4(),ShowList5(),ShowList6();
		 int FindNumber(long);
		 long check(char);
		 int number,i;
		 long num=0;
		 char val;
		 char ch;
		 char numstr[10];
		 while(1)
		 {
				 Clear();
				 music();
				 FirstScreen();
				 Clear();
				 music();
				 val=ShowList1();
				 num=check(val);
				 Clear();
				 music();
				 val=ShowList2();
				 num=num*10+check(val);
				 Clear();
				 music();
				 val=ShowList3();
				 num=num*10+check(val);
				 Clear();
				 music();
				 val=ShowList4();
				 num=num*10+check(val);
				 Clear();
				 music();
				 val=ShowList5();
				 num=num*10+check(val);
				 Clear();
				 music();
				 val=ShowList6();
				 num=num*10+check(val);
				 number=FindNumber(num);
				 itoa(number,numstr,10);
				 Clear();
				 music();
				 settextstyle(5,0,4);
				 settextjustify(0,1);
				 if (number)
				 {
						 outtextxy(100,150,"So the number you thought was...");
						 setcolor(14);
						 settextstyle(4,0,15);
						 settextjustify(1,1);
						 outtextxy(320,250,numstr);
						 setcolor(15);
						 settextstyle(6,0,4);
						 outtextxy(320,350,"Can't believe it .........");
				 }
				 else
				 {
						 setcolor(14);
						 outtextxy(100,180,"Your number is out of range ...");
						 outtextxy(200,260,"OR....");
						 outtextxy(100,340,"You did not answer properly !!! ");
				 }
				 settextjustify(1,1);
				 settextstyle(6,0,4);
				 setcolor(CYAN);
				 outtextxy(320,400,"Wish to Try again (y/n) !!!!");
				 ch=getch();
				 if (ch=='y'||ch=='Y')
				 {
				    outtextxy(510,400,"Y");
				    music();
				    getch();
				 }
				 else
				 {
				    outtextxy(510,400,"N");
				    getch();
				    music();
				    return;
				 }
		 }
}

void DisplayName(int ycor)
{
		 char *name[] = {"M","A","G","I","C"," ","N","U","M","B","E","R"};
		 int i;
		 settextjustify(1,1);
		 settextstyle(4,0,7);
		 for(i=0;i<12;i++)
		 {
				 setcolor(i+2);
				 outtextxy(40+i*45,ycor, name[i]);
		 }
}
void Clear()
{
		 setfillstyle(8,BLUE);
		 bar(0,0,640,480);
		 DisplayName(30);
}
//Displaying the first Game Screen
void FirstScreen()
{
		 settextjustify(1,1);
		 setcolor(2);
		 settextstyle(1,0,4);
		 outtextxy(320,150," Think of any number in the range ");
		 setcolor(14);
		 settextstyle(4,0,8);
		 outtextxy(320,250,"1 - 55");
		 settextstyle(5,0,3);
		 setcolor(CYAN);
		 outtextxy(320,350,"Press any key to continue ......");
		 setcolor(15);
		 settextstyle(3,0,3);
		 outtextxy(320,430,"And Please... Be Honest !!!!!");
		 getch();
}
//Displaying the six lists
char ShowList1()
{
		 char ch;
		 setcolor(14);
		 settextstyle(3,0,4);
		 settextjustify(0,1);
		 outtextxy(70,120,"1,  3, 4, 7, 8, 11, 12");
		 outtextxy(70,180,"14, 16, 17, 18, 19, 20");
		 outtextxy(70,240,"24, 25, 28, 30, 31, 33");
		 outtextxy(70,300,"35, 37, 40, 42, 44, 46");
		 outtextxy(70,360,"47, 48, 50, 52, 54, 55");
		 settextstyle(5,0,3);
		 setcolor(2);
		 outtextxy(30,420,"Does Your number appear here ? (y/n)...");
		 ch=getch();
		 fflush(stdin);
		 if (ch=='y'||ch=='Y')
				 outtextxy(500,420,"Y");
		 else
				 outtextxy(500,420,"N");
		 getch();
		 return(ch);
		 }
char ShowList2()
{
		 char ch;
		 setcolor(14);
		 settextstyle(3,0,4);
		 settextjustify(0,1);
		 outtextxy(70,120,"1, 3, 6, 8, 10, 11, 12");
		 outtextxy(70,180,"15, 17, 18, 19, 22, 23");
		 outtextxy(70,240,"26, 29, 31, 32, 33, 34");
		 outtextxy(70,300,"36, 37, 38, 41, 44, 45");
		 outtextxy(70,360,"47, 50, 51, 53, 54, 55");
		 settextstyle(5,0,3);
		 setcolor(2);
		 outtextxy(30,420,"How about here ? (y/n)...");
		 ch=getch();
		 fflush(stdin);
		 if (ch=='y'||ch=='Y')
				 outtextxy(500,420,"Y");
		 else
				 outtextxy(500,420,"N");
		 getch();
		 return(ch);
}

char ShowList3()
{
		 char ch;
		 setcolor(14);
		 settextstyle(3,0,4);
		 settextjustify(0,1);
		 outtextxy(70,120,"1,  2,  5,  6,  7,  10");
		 outtextxy(70,180,"11, 13, 15, 16, 17, 19");
		 outtextxy(70,240,"21, 22, 24, 26, 27, 28");
		 outtextxy(70,300,"32, 35, 38, 40, 44, 46");
		 outtextxy(70,360,"47, 48, 49, 53, 54, 55");
		 settextstyle(5,0,3);
		 setcolor(2);
		 outtextxy(30,420,"Now here ? (y/n)...");
		 ch=getch();
		 if (ch=='y'||ch=='Y')
				 outtextxy(500,420,"Y");
		 else
				 outtextxy(500,420,"N");
		 fflush(stdin);
		 getch();
		 return(ch);
}
char ShowList4()
{
		 char ch;
		 setcolor(14);
		 settextstyle(3,0,4);
		 settextjustify(0,1);
		 outtextxy(70,120,"1, 2, 5, 9, 13, 17, 18");
		 outtextxy(70,180,"20, 22, 25, 26, 28, 30");
		 outtextxy(70,240,"31, 32, 33, 35, 36, 37");
		 outtextxy(70,300,"38, 39, 40, 41, 42, 43");
		 outtextxy(70,360,"45, 46, 49, 51, 54, 55");
		 settextstyle(5,0,3);
		 setcolor(2);
		 outtextxy(30,420,"And here ? (y/n)...");
		 ch=getch();
		 fflush(stdin);
		 if (ch=='y'||ch=='Y')
				 outtextxy(500,420,"Y");
		 else
				 outtextxy(500,420,"N");
		 getch();
		 return(ch);
}
char ShowList5()
{
		 char ch;
		 setcolor(14);
		 settextstyle(3,0,4);
		 settextjustify(0,1);
		 outtextxy(70,120,"  4,   5,   8,   9,  10");
		 outtextxy(70,180,"11, 12, 13, 14, 15, 16");
		 outtextxy(70,240,"19, 21, 24, 27, 29, 30");
		 outtextxy(70,300,"32, 33, 34, 37, 38, 40");
		 outtextxy(70,360,"42, 45, 46, 51, 54, 55");
		 settextstyle(5,0,3);
		 setcolor(2);
		 outtextxy(30,420,"And here ? (y/n)...");
		 fflush(stdin);
		 ch=getch();
		 if (ch=='y'||ch=='Y')
				 outtextxy(500,420,"Y");
		 else
				 outtextxy(500,420,"N");
		 getch();
		 return(ch);
}
char ShowList6()
{
		 char ch;
		 setcolor(14);
		 settextstyle(3,0,4);
		 settextjustify(0,1);
		 outtextxy(70,120," 2,   3,    6,   7,  9");
		 outtextxy(70,180,"12, 13, 14, 15, 17, 19");
		 outtextxy(70,240,"23, 24, 25, 26, 27, 31");
		 outtextxy(70,300,"34, 35, 37, 38, 41, 42");
		 outtextxy(70,360,"43, 46, 47, 51, 52, 55");
		 settextstyle(5,0,3);
		 setcolor(2);
		 outtextxy(30,420,"Finally here ? (y/n)...");
		 ch=getch();
		 fflush(stdin);
		 if (ch=='y'||ch=='Y')
				 outtextxy(500,420,"Y");
		 else
				 outtextxy(500,420,"N");
		 getch();
		 return(ch);
}
int FindNumber(long num)
{
				 switch(num)
				 {
						 case 111100		 :  return (1);
						 case 1101		 :  return (2);
						 case 110001		 :  return (3);
						 case 100010		 :  return (4);
						 case 1110		 :  return (5);
						 case 11001		 :  return (6);
						 case 101001		 :  return (7);
						 case 110010		 :  return (8);
						 case 111		 :  return (9);
						 case 11010		 :  return(10);
						 case 111010		 :  return(11);
						 case 110011		 :  return(12);
						 case 1111		 :  return(13);
						 case 100011		 :  return(14);
						 case 11011		 :  return(15);
						 case 101010		 :  return(16);
						 case 111101		 :  return(17);
						 case 110100		 :  return(18);
						 case 111011		 :  return(19);
						 case 100100		 :  return(20);
						 case 1010		 :  return(21);
						 case 11100		 :  return(22);
						 case 10001		 :  return(23);
						 case 101011		 :  return(24);
						 case 100101		 :  return(25);
						 case 11101		 :  return(26);
						 case 1011		 :  return(27);
						 case 101100		 :  return(28);
						 case 10010		 :  return(29);
						 case 100110		 :  return(30);
						 case 110101		 :  return(31);
						 case 11110		 :  return(32);
						 case 110110		 :  return(33);
						 case 10011		 :  return(34);
						 case 101101		 :  return(35);
						 case 10100		 :  return(36);
						 case 110111		 :  return(37);
						 case 11111		 :  return(38);
						 case 100		 :  return(39);
						 case 101110		 :  return(40);
						 case 10101		 :  return(41);
						 case 100111		 :  return(42);
						 case 101		 :  return(43);
						 case 111000		 :  return(44);
						 case 10110		 :  return(45);
						 case 101111		 :  return(46);
						 case 111001		 :  return(47);
						 case 101000		 :  return(48);
						 case 1100		 :  return(49);
						 case 110000		 :  return(50);
						 case 10111		 :  return(51);
						 case 100001		 :  return(52);
						 case 11000		 :  return(53);
						 case 111110		 :  return(54);
						 case 111111		 :  return(55);
						 default		 		 :  return(0);
				 }
}

long check(char ch)
  {
		 if (ch=='y'||ch=='Y')
				 return(1);
		 else
				 return(0);
  }

music()
{
int i  ;
float octave[7] = { 130.81, 146.83, 164.81, 174.61, 196, 220, 246.94 } ;
		 for ( i = 0 ; i < 7 ; i++ )
						 {
								 sound ( octave[i] * 8 ) ;
								 delay ( 30 ) ;
						 }
		nosound();
}
