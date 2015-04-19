#include<simplecpp>
#include<fstream>
#include<string>

void update_hs(int levelno, int score1)  //This function implements updating the high score file and shows "High Score" in a level if the user has made
{                                        //a new high score. It updates an array of the previous high scores and then prints it in the file.
    levelno=levelno-1;
    int temp;
    int hs[20];
    ofstream out;
    ifstream in;

    in.open("high score.txt",ios::in);
    for(int i=0; i<=19; i++)
    {
        in>>temp;
        hs[i]=temp;
        if(score1<=hs[levelno])
        {
            Text hst(300,50,"High Score!!");
            hst.setFill(1);
            hst.setColor(COLOR("blue"));
            hst.imprint();
            hst.hide();
            hs[levelno]=score1;
        }

    }
    in.close();
    out.open("high score.txt",ios::ate);
    for(int i=0; i<20; i++)
    {
        out<<hs[i]<<endl;
    }
}

void clearall()  //TO CLEAR THE SCREEN WHENEVER REQUIRED
{
    Rectangle clear1(300,300,600,600);
    clear1.setFill(1);
    clear1.setColor(COLOR("white"));
    clear1.imprint();
    clear1.hide();
}

class unblkme   //This class contains all the functions, arrays and variables needed to build a level.
{
private:
    int originallevela[120][6]=                                 //This contains the information of position of the blocks for all the twenty levels
    {
        {2,2,2,0,0,2},{0,0,2,0,0,2},{3,3,2,0,0,2},{1,0,2,0,1,1},{1,0,0,0,1,0},{2,2,2,0,1,0}
        ,{0,0,2,0,1,1},{0,0,2,0,0,2},{3,3,2,0,0,2},{0,1,2,2,2,2},{0,1,1,1,1,0},{0,0,0,0,1,0}
        ,{1,1,1,1,1,0},{1,0,1,0,0,0},{3,3,1,2,2,0},{0,0,0,2,2,0},{2,2,2,2,2,0},{0,0,0,0,0,0}
        ,{0,0,0,0,0,0},{0,2,2,2,0,1},{3,3,1,2,0,1},{0,0,1,2,1,1},{2,2,2,2,0,1},{0,0,0,0,0,1}
        ,{0,0,0,0,0,0},{1,0,0,1,2,1},{1,3,3,1,2,1},{1,1,1,1,2,0},{0,1,1,2,2,2},{0,1,1,1,1,0}
        ,{0,1,1,1,0,0},{0,1,1,1,2,0},{0,2,3,3,2,0},{0,2,1,1,2,2},{0,2,1,0,0,2},{1,1,1,1,1,2}
        ,{0,0,1,1,0,0},{0,0,1,1,0,1},{3,3,1,1,2,1},{1,1,1,1,2,0},{1,1,1,1,2,0},{1,1,0,0,0,0}
        ,{0,0,0,0,0,1},{1,1,2,0,0,1},{0,0,2,3,3,1},{1,1,2,1,0,1},{1,1,1,1,1,1},{1,1,1,0,0,0}
        ,{1,1,1,1,0,1},{1,1,1,1,1,2},{1,2,1,3,3,2},{1,2,1,1,0,0},{1,2,1,1,1,1},{0,0,1,2,2,2}
        ,{0,1,0,0,0,1},{0,1,2,2,2,1},{3,3,1,1,2,1},{0,0,1,1,2,1},{1,0,1,1,2,0},{1,1,1,1,1,0}
        ,{1,1,1,2,1,1},{1,0,2,2,0,0},{3,3,2,2,0,0},{0,0,2,1,1,2},{0,0,0,0,0,2},{1,1,0,0,0,2}
        ,{2,2,2,0,1,0},{0,0,0,0,1,1},{3,3,0,0,1,1},{1,1,1,1,1,0},{1,0,0,1,1,1},{0,0,0,0,0,0}
        ,{1,1,2,2,2,0},{1,1,1,1,1,0},{3,3,1,1,0,0},{0,0,1,1,1,1},{1,1,1,1,1,1},{0,1,1,0,0,1}
        ,{0,0,1,1,1,0},{0,1,1,0,0,2},{0,1,3,3,1,2},{2,2,2,0,1,2},{0,1,2,2,2,0},{0,1,1,1,1,1}
        ,{1,0,1,1,1,1},{1,0,1,0,0,1},{3,3,1,0,0,1},{1,0,1,1,1,1},{1,1,1,1,0,0},{0,0,0,1,0,0}
        ,{1,1,1,2,0,0},{1,1,1,2,0,0},{2,3,3,2,0,0},{2,2,2,2,0,0},{2,1,1,0,0,0},{2,2,2,0,0,0}
        ,{0,2,0,0,2,0},{0,2,0,0,2,1},{0,2,3,3,2,1},{0,0,1,1,1,1},{0,0,1,1,0,1},{2,2,2,1,0,0}
        ,{0,2,0,0,2,0},{0,2,0,0,2,1},{0,2,3,3,2,1},{0,0,1,1,1,1},{0,0,1,1,0,1},{2,2,2,1,0,0}
        ,{1,1,2,1,1,0},{1,1,2,1,1,0},{3,3,2,0,1,0},{1,0,1,1,1,2},{1,0,0,1,1,2},{2,2,2,1,1,2}
        ,{1,1,1,1,1,1},{1,0,1,1,1,1},{3,3,1,0,1,0},{1,1,1,1,1,0},{2,2,2,1,0,0},{0,0,0,1,0,0}
    };
    char originallevelb[120][6]=                //This contains the information of the orientation of the blocks in all the twenty levels.
    {

        {'l','h','r',0,0,'t'},{0,0,'t',0,0,'v'},{'l','r','v',0,0,'b'},{'t',0,'b',0,'l','r'},{'b',0,0,0,'t',0},{'l','h','r',0,'b',0},
        {0,0,'t',0,'l','r'},{0,0,'v',0,0,'t'},{'l','r','b',0,0,'v'},{0,'t','l','h','r','b'},{0,'b','l','r','t',0},{0,0,0,0,'b',0},
        {'t','l','r','l','r',0},{'b',0,'t',0,0,0},{'l','r','b','t','t',0},{0,0,0,'v','v',0},{'l','h','r','b','b',0},{0,0,0,0,0,0},
        {0,0,0,0,0,0},{0,'l','h','r',0,'t'},{'l','r','t','t',0,'b'},{0,0,'b','v','l','r'},{'l','h','r','b',0,'t'},{0,0,0,0,0,'b'},
        {0,0,0,0,0,0},{'t',0,0,'t','t','t'},{'b','l','r','b','v','b'},{'l','r','l','r','b',0},{0,'t','t','l','h','r'},{0,'b','b','l','r',0},
        {0,'l','r','t',0,0},{0,'l','r','b','t',0},{0,'t','l','r','v',0},{0,'v','l','r','b','t'},{0,'b','t',0,0,'v'},{'l','r','b','l','r','b'},
        {0,0,'t','t',0,0},{0,0,'b','b',0,'t'},{'l','r','t','t','t','b'},{'l','r','b','b','v',0},{'t','t','l','r','b',0},{'b','b',0,0,0,0},
        {0,0,0,0,0,'t'},{'l','r','t',0,0,'b'},{0,0,'v','l','r','t'},{'l','r','b','t',0,'b'},{'t','l','r','b','l','r'},{'b','l','r',0,0,0},
        {'l','r','l','r',0,'t'},{'t','l','r','l','r','v'},{'b','t','t','l','r','b'},{'t','v','b','t',0,0},{'b','b','t','b','l','r'},{0,0,'b','l','h','r'},
        {0,'t',0,0,0,'t'},{0,'b','l','h','r','b'},{'l','r','t','t','t','t'},{0,0,'b','b','v','b'},{'t',0,'l','r','b',0},{'b','l','r','l','r',0},
        {'t','l','r','t','l','r'},{'b',0,'t','v',0,0},{'l','r','v','b',0,0},{0,0,'b','l','r','t'},{0,0,0,0,0,'v'},{'l','r',0,0,0,'b'}
        ,{'l','h','r',0,'t',0},{0,0,0,0,'b','t'},{'l','r',0,0,'t','b'},{'t','l','r','t','b',0},{'b',0,0,'b','l','r'},{0,0,0,0,0,0}
        ,{'t','t','l','h','r',0},{'b','b','t','l','r',0},{'l','r','b','t',0,0},{0,0,'t','b','l','r'},{'l','r','b','l','r','t'},{0,'l','r',0,0,'b'}
        ,{0,0,'t','l','r',0},{0,'t','b',0,0,'t'},{0,'b','l','r','t','v'},{'l','h','r',0,'b','b'},{0,'t','l','h','r',0},{0,'b','l','r','l','r'}
        ,{'t',0,'t','l','r','t'},{'b',0,'b',0,0,'b'},{'l','r','t',0,0,'t'},{'t',0,'b','l','r','b'},{'b','l','r','t',0,0},{0,0,0,'b',0,0}
        ,{'l','r','t','t',0,0},{'l','r','b','v',0,0},{'t','l','r','b',0,0},{'v','l','h','r',0,0},{'b','l','r',0,0,0},{'l','h','r',0,0,0},
        {0,'t',0,0,'t',0},{0,'v',0,0,'v','t'},{0,'b','l','r','b','b'},{0,0,'t','l','r','t'},{0,0,'b','t',0,'b'},{'l','h','r','b',0,0},
        {0,'t',0,0,'t',0},{0,'v',0,0,'v','t'},{0,'b','l','r','b','b'},{0,0,'t','l','r','t'},{0,0,'b','t',0,'b'},{'l','h','r','b',0,0},
        {'t','t','t','l','r',0},{'b','b','v','l','r',0},{'l','r','b',0,'t',0},{'t',0,'l','r','b','t'},{'b',0,0,'t','t','v'},{'l','h','r','b','b','b'},
        {'t','l','r','l','r','t'},{'b',0,'l','r','t','b'},{'l','r','t',0,'b',0},{'l','r','b','l','r',0},{'l','h','r','t',0,0},{0,0,0,'b',0,0}
    };

    int levelno;       //To specify the level number where ever required

public:
    int no_of_steps;       //To count the number of steps the user has made in a level
    int levela[6][6];       //On selecting a level number, this array copies the corresponding elements from the original arrays and
    char levelb[6][6];      //this array is then later on used for running the game. This algorithm was used becuase if the user wants to reset the game,
                            // then we can use the original arrays
    void init_level(int level_no)               //COPIES THE RESPECTIVE DATA ACCORDING TO THE LEVEL NUMBER TO THE ARRAYS WE WILL BE MODIFYING
    {
        levelno=level_no;
        no_of_steps=0;
        for(int i=1; i<=20; i++)
        {
            if(levelno==i)
            {
                for(int j=0; j<6; j++)
                {
                    for(int k=0; k<6; k++)
                    {
                        levela[j][k]=originallevela[j+6*(levelno-1)][k];
                        levelb[j][k]=originallevelb[j+6*(levelno-1)][k];
                    }
                }
            }
        }
    }

    bool isAllowed( int i,int j)       //This function checks whether the selected movement of a block is valid or not
    {
        if(j!=0 && levelb[i][j]=='l' && levelb[i][j-1]==0 && i>=0 && i<=5 && j<=5) return 1;
        else if( j!=5 && levelb[i][j]=='r' && levelb[i][j+1]==0 && i>=0 && i<=5 && j>=0 ) return 1;
        else if(i!=0 && levelb[i][j]=='t' && levelb[i-1][j]==0 && j>=0 && j<=5 && i<=5) return 1;
        else if(i!=5 && levelb[i][j]=='b' && levelb[i+1][j]==0 && i>=0 && i<=5 && j>=0 ) return 1;
        else return 0;
    }

    void update_array_to_move(int m, int n)  //If the movement is valid, then it updates the arrays to build the level again
    {
        if(levela[m][n]==1 && levelb[m][n]=='l')
        {
            if(n!=0)
            {
                levelb[m][n+1]=0;
                levela[m][n+1]=0;
                levela[m][n]=1;
                levela[m][n-1]=1;
                levelb[m][n]='r';
                levelb[m][n-1]='l';
            }
        }
        else if(levela[m][n]==1 && levelb[m][n]=='r')
        {
            if(n!=5)
            {
                levela[m][n-1]=0;
                levelb[m][n-1]=0;
                levela[m][n]=1;
                levela[m][n+1]=1;
                levelb[m][n]='l';
                levelb[m][n+1]='r';
            }
        }
        else if(levela[m][n]==1&&levelb[m][n]=='t')
        {
            if(m!=0)
            {
                levela[m+1][n]=0;
                levelb[m+1][n]=0;
                levela[m][n]=1;
                levela[m-1][n]=1;
                levelb[m][n]='b';
                levelb[m-1][n]='t';
            }
        }
        else if(levela[m][n]==1&&levelb[m][n]=='b')
        {
            if(m!=5)
            {
                levela[m-1][n]=0;
                levelb[m-1][n]=0;
                levela[m][n]=1;
                levela[m+1][n]=1;
                levelb[m][n]='t';
                levelb[m+1][n]='b';
            }
        }
        else if(levela[m][n]==2 && levelb[m][n]=='l')
        {
            if(n!=0)
            {
                levela[m][n+2]=0;
                levelb[m][n+2]=0;
                levela[m][n-1]=2;
                levela[m][n]=2;
                levela[m][n+1]=2;
                levelb[m][n-1]='l';
                levelb[m][n]='h';
                levelb[m][n+1]='r';
            }
        }
        else if(levela[m][n]==2 && levelb[m][n]=='r')
        {
            if(n!=5)
            {
                levela[m][n-2]=0;
                levelb[m][n-2]=0;
                levela[m][n-1]=2;
                levela[m][n]=2;
                levela[m][n+1]=2;
                levelb[m][n-1]='l';
                levelb[m][n]='h';
                levelb[m][n+1]='r';
            }
        }
        else if(levela[m][n]==2 && levelb[m][n]=='t')
        {
            if(m!=0)
            {
                levela[m+2][n]=0;
                levelb[m+2][n]=0;
                levela[m-1][n]=2;
                levela[m][n]=2;
                levela[m+1][n]=2;
                levelb[m-1][n]='t';
                levelb[m][n]='v';
                levelb[m+1][n]='b';
            }
        }
        else if(levela[m][n]==2&& levelb[m][n]=='b')
        {
            if(m!=5)
            {
                levela[m-2][n]=0;
                levelb[m-2][n]=0;
                levela[m-1][n]=2;
                levela[m][n]=2;
                levela[m+1][n]=2;
                levelb[m-1][n]='t';
                levelb[m][n]='v';
                levelb[m+1][n]='b';
            }
        }
        else if(levela[m][n]==3 && levelb[m][n]=='l')
        {
            if(n!=0)
            {
                levelb[m][n+1]=0;
                levela[m][n+1]=0;
                levela[m][n]=3;
                levela[m][n-1]=3;
                levelb[m][n]='r';
                levelb[m][n-1]='l';
            }
        }
        else if(levela[m][n]==3 && levelb[m][n]=='r')
        {
            if(n!=5)
            {
                levela[m][n-1]=0;
                levelb[m][n-1]=0;
                levela[m][n]=3;
                levela[m][n+1]=3;
                levelb[m][n]='l';
                levelb[m][n+1]='r';
            }
        }
        else
        {
            return;
        }
    }

    void buildlevel()             //This function builds the graphics for the levels and builds the blocks from the corresponding arrays
    {
        beginFrame();
        {
            //DISPLYING ALL THE ARBIT BOXES OF MENU, RESET, NO OF STEPS
            Rectangle brown1(300,300,420,420);
            brown1.setFill(1);
            brown1.setColor(COLOR(139,90,43));
            brown1.imprint();
            Rectangle peach(300,300,600,600);
            peach.setFill(1);
            peach.setColor(COLOR(237,253,161)), peach.imprint();
            Rectangle black(300,300,440,440);
            black.setFill(1);
            black.setColor(COLOR("black"));
            black.imprint();
            Rectangle rmoves(555,45,50,50);
            Text tmoves(555,30,"MOVES");
            Rectangle menu(45,45,50,50);
            Text tmenu(45,45,"MENU");
            Rectangle reset(555,555,50,50);
            Text treset(555,555,"RESET");
            Text tnosteps(555,50,no_of_steps);
            Rectangle level(45,555,50,50);
            Text tlevel(45,555,"LEVEL NO.");
            level.imprint();
            tlevel.imprint();
            tnosteps.imprint();  //setting the reset box
            reset.imprint();
            treset.imprint();
            brown1.imprint();
            rmoves.imprint();
            tmoves.imprint();
            menu.imprint();
            tmenu.imprint();
            Rectangle blank(520,265,15,70);
            blank.setFill(1);
            blank.setColor(COLOR(237,253,161));
            blank.imprint();

        }                            //AND THEN BUILDING THE LEVEL
        for(int i=0; i<=5; i++)
        {
            for(int j=0; j<=5; j++)
            {
                if(levela[i][j]==3)
                {
                    if(levelb[i][j]=='l')
                    {
                        Rectangle r1(126+70*j,125+70*i,68,66);
                        r1.setFill(1);
                        r1.setColor(COLOR("red"));
                        r1.imprint();
                    }
                    if(levelb[i][j]=='r')
                    {

                        Rectangle r1(124+70*j,125+70*i,68,66);
                        r1.setFill(1);
                        r1.setColor(COLOR("red"));
                        r1.imprint();
                    }
                }
                else
                {

                    if(levelb[i][j]=='l')
                    {

                        Rectangle r1(126+70*j,125+70*i,68,66);
                        r1.setFill(1);
                        r1.setColor(COLOR("yellow"));
                        r1.imprint();
                    }
                    if(levelb[i][j]=='r')
                    {

                        Rectangle r1(124+70*j,125+70*i,68,66);
                        r1.setFill(1);
                        r1.setColor(COLOR("yellow"));
                        r1.imprint();
                    }
                    if(levelb[i][j]=='t')
                    {

                        Rectangle r1(125+70*j,126+70*i,66,66);
                        r1.setFill(1);
                        r1.setColor(COLOR("yellow"));
                        r1.imprint();
                    }
                    if(levelb[i][j]=='b')
                    {

                        Rectangle r1(125+70*j,124+70*i,66,66);
                        r1.setFill(1);
                        r1.setColor(COLOR("yellow"));
                        r1.imprint();
                    }
                    if(levelb[i][j]=='h')
                    {

                        Rectangle r1(125+70*j,125+70*i,70,66);
                        r1.setFill(1);
                        r1.setColor(COLOR("yellow"));
                        r1.imprint();
                    }
                    if(levelb[i][j]=='v')
                    {

                        Rectangle r1(125+70*j,125+70*i,66,70);
                        r1.setFill(1);
                        r1.setColor(COLOR("yellow"));
                        r1.imprint();
                    }
                }

            }
        }
        endFrame();
    }

    void buildlevel_after(int i,int j)        //This function takes the coordinates from the click and then shows the "updated" level
    {
        if(isAllowed(i,j))
        {

            no_of_steps++;
            update_array_to_move(i,j);    //UPDATING THE ARRAY
            buildlevel();                //BUILDING THE UPDATED ARRAY
        }
        else if(i==6 && j==6)           //IF CLICKED ON RESET, RESETS THE LEVEL AND PUTS THE BLOCKS IN INITIAL POSITION AND SETS NUMBER OF STEPS TO 0
        {
            no_of_steps=0;
            Rectangle r1(555,50,40,20);
            r1.setFill(1);
            r1.setColor(COLOR("white"));
            r1.imprint();
            Text t1(555,50,no_of_steps);
            t1.imprint();
            init_level(levelno);
            buildlevel();
        }
        else                        //SHOWS THE USER THAT HE HAS MADE AN INVALID MOVE
        {
            Text inv(200,20,"INVALID MOVE");
            wait(0.5);
            inv.hide();
        }
    }

};  //UNBLOCK ME CLASS ENDS HERE

class menu_level             //This class is built for dealing with graphics and working of Menu page, Level page, High score page and How to play page
{

public:
    int xnext1,ynext1,xnext2,ynext2,xnext3,ynext3;

    void build_menu()                     //BUILD THE GRAPHICS FOR MENU
    {
        beginFrame();
        clearall();                      //CLEAR THE FULL SCREEN AND THEN DISPLAYING THE MENU
        Rectangle play(300,200,200,50); //play.setFill(1); play.setColor(COLOR(255,200,230));
        Text tplay(300,200,"PLAY");
        play.setFill(1);
        play.setColor(COLOR(128,0,0));
        play.imprint();
        Rectangle htp(300,300,200,50);
        htp.setFill(1);
        htp.setColor(COLOR(128,0,0));
        htp.imprint();
        Text thtp(300,300,"HOW TO PLAY");
        Rectangle hs(300,400,200,50);
        hs.setFill(1);
        hs.setColor(COLOR(128,0,0));
        hs.imprint();
        Text ths(300,400,"HIGH SCORE");
        Rectangle exit(300,500,200,50);
        Text texit(300,500,"EXIT");
        exit.setFill(1);
        exit.setColor(COLOR(128,0,0));
        exit.imprint();
        endFrame();
        beginFrame();

         {    //menu ends   //building if the rectangles
           Rectangle r10(50,25,100,50),r20(50,75,100,50),r30(50,125,100,50),r40(50,175,100,50),r50(50,225,100,50),r60(50,275,100,50),
           r70(50,325,100,50),r80(50,375,100,50),r90(50,425,100,50),r100(50,475,100,50),r110(50,525,100,50),r120(50,575,100,50),

           r11(150,25,100,50),r21(150,75,100,50),r31(150,125,100,50),r41(150,175,100,50),r51(150,225,100,50),r61(150,275,100,50),
           r71(150,325,100,50),r81(150,375,100,50),r91(150,425,100,50),r101(150,475,100,50),r111(150,525,100,50),r121(150,575,100,50),

           r12(250,25,100,50),r22(250,75,100,50),r32(250,125,100,50),r42(250,175,100,50),r52(250,225,100,50),r62(250,275,100,50),
           r72(250,325,100,50),r82(250,375,100,50),r92(250,425,100,50),r102(250,475,100,50),r112(250,525,100,50),r122(250,575,100,50),

           r13(350,25,100,50),r23(350,75,100,50),r33(350,125,100,50),r43(350,175,100,50),r53(350,225,100,50),r63(350,275,100,50),
           r73(350,325,100,50),r83(350,375,100,50),r93(350,425,100,50),r103(350,475,100,50),r113(350,525,100,50),r123(350,575,100,50),

           r14(450,25,100,50),r24(450,75,100,50),r34(450,125,100,50),r44(450,175,100,50),r54(450,225,100,50),r64(450,275,100,50),
           r74(450,325,100,50),r84(450,375,100,50),r94(450,425,100,50),r104(450,475,100,50),r114(450,525,100,50),r124(450,575,100,50),

           r15(550,25,100,50),r25(550,75,100,50),r35(550,125,100,50),r45(550,175,100,50),r55(550,225,100,50),r65(550,275,100,50),
           r75(550,325,100,50),r85(550,375,100,50),r95(550,425,100,50),r105(550,475,100,50),r115(550,525,100,50),r125(550,575,100,50);

           r10.setFill(1);r20.setFill(1);r30.setFill(1);r40.setFill(1);r50.setFill(1);r60.setFill(1);
           r70.setFill(1);r80.setFill(1);r90.setFill(1);r100.setFill(1);r110.setFill(1);r120.setFill(1);

           r11.setFill(1);r21.setFill(1);r31.setFill(1);r41.setFill(1);r51.setFill(1);r61.setFill(1);
           r71.setFill(1);r81.setFill(1);r91.setFill(1);r101.setFill(1);r111.setFill(1);r121.setFill(1);

           r12.setFill(1);r22.setFill(1);r32.setFill(1);r42.setFill(1);r52.setFill(1);r62.setFill(1);
           r72.setFill(1);r82.setFill(1);r92.setFill(1);r102.setFill(1);r112.setFill(1);r122.setFill(1);

           r13.setFill(1);r23.setFill(1);r33.setFill(1);r43.setFill(1);r53.setFill(1);r63.setFill(1);
           r73.setFill(1);r83.setFill(1);r93.setFill(1);r103.setFill(1);r113.setFill(1);r123.setFill(1);

           r14.setFill(1);r24.setFill(1);r34.setFill(1);r44.setFill(1);r54.setFill(1);r64.setFill(1);
           r74.setFill(1);r84.setFill(1);r94.setFill(1);r104.setFill(1);r114.setFill(1);r124.setFill(1);

           r15.setFill(1);r25.setFill(1);r35.setFill(1);r45.setFill(1);r55.setFill(1);r65.setFill(1);
           r75.setFill(1);r85.setFill(1);r95.setFill(1);r105.setFill(1);r115.setFill(1);r125.setFill(1);

           r10.setColor(COLOR(148,255,187));r20.setColor(COLOR(235,216,257));r30.setColor(COLOR(224,227,286));r40.setColor(COLOR(237,253,261));r50.setColor(COLOR(215,219,236));r60.setColor(COLOR(241,225,210));
           r70.setColor(COLOR(194,198,53));r80.setColor(COLOR(15,219,236));r90.setColor(COLOR(145,69,228));r100.setColor(COLOR(141,109,116));r110.setColor(COLOR(237,153,61));r120.setColor(COLOR(114,78,173));

           r11.setColor(COLOR(234,228,17));r21.setColor(COLOR(145,69,228));r31.setColor(COLOR(240,11,11));r41.setColor(COLOR(35,216,57));r51.setColor(COLOR(232,19,216));r61.setColor(COLOR(234,228,17));
           r71.setColor(COLOR(15,219,236));r81.setColor(COLOR(145,69,228));r91.setColor(COLOR(208,60,43));r101.setColor(COLOR(194,198,53));r111.setColor(COLOR(241,125,10));r121.setColor(COLOR(237,153,61));

           r12.setColor(COLOR(48,230,187));r22.setColor(COLOR(35,216,57));r32.setColor(COLOR(224,27,86));r42.setColor(COLOR(237,153,61));r52.setColor(COLOR(15,219,236));r62.setColor(COLOR(241,125,10));
           r72.setColor(COLOR(194,198,53));r82.setColor(COLOR(15,219,236));r92.setColor(COLOR(145,69,228));r102.setColor(COLOR(141,109,116));r112.setColor(COLOR(237,153,61));r122.setColor(COLOR(114,78,173));

           r13.setColor(COLOR(234,228,17));r23.setColor(COLOR(145,69,228));r33.setColor(COLOR(240,11,11));r43.setColor(COLOR(35,216,57));r53.setColor(COLOR(232,19,216));r63.setColor(COLOR(234,228,17));
           r73.setColor(COLOR(15,219,236));r83.setColor(COLOR(145,69,228));r93.setColor(COLOR(208,60,43));r103.setColor(COLOR(194,198,53));r113.setColor(COLOR(241,125,10));r123.setColor(COLOR(237,153,61));

           r14.setColor(COLOR(48,230,187));r24.setColor(COLOR(35,216,57));r34.setColor(COLOR(224,27,86));r44.setColor(COLOR(237,153,61));r54.setColor(COLOR(15,219,236));r64.setColor(COLOR(241,125,10));
           r74.setColor(COLOR(194,198,53));r84.setColor(COLOR(15,219,236));r94.setColor(COLOR(145,69,228));r104.setColor(COLOR(141,109,116));r114.setColor(COLOR(237,153,61));r124.setColor(COLOR(114,78,173));

           r15.setColor(COLOR(234,228,17));r25.setColor(COLOR(145,69,228));r35.setColor(COLOR(240,11,11));r45.setColor(COLOR(35,216,57));r55.setColor(COLOR(232,19,216));r65.setColor(COLOR(234,228,17));
           r75.setColor(COLOR(15,219,236));r85.setColor(COLOR(145,69,228));r95.setColor(COLOR(208,60,43));r105.setColor(COLOR(194,198,53));r115.setColor(COLOR(241,125,10));r125.setColor(COLOR(237,153,61));

           r10.imprint();r20.imprint();r30.imprint();r40.imprint();r50.imprint();r60.imprint();
           r70.imprint();r80.imprint();r90.imprint();r100.imprint();r110.imprint();r120.imprint();

           r11.imprint();r21.imprint();r31.imprint();r41.imprint();r51.imprint();r61.imprint();
           r71.imprint();r81.imprint();r91.imprint();r101.imprint();r111.imprint();r121.imprint();

           r12.imprint();r22.imprint();r32.imprint();r42.imprint();r52.imprint();r62.imprint();
           r72.imprint();r82.imprint();r92.imprint();r102.imprint();r112.imprint();r122.imprint();

           r13.imprint();r23.imprint();r33.imprint();r43.imprint();r53.imprint();r63.imprint();
           r73.imprint();r83.imprint();r93.imprint();r103.imprint();r113.imprint();r123.imprint();

           r14.imprint();r24.imprint();r34.imprint();r44.imprint();r54.imprint();r64.imprint();
           r74.imprint();r84.imprint();r94.imprint();r104.imprint();r114.imprint();r124.imprint();

           r15.imprint();r25.imprint();r35.imprint();r45.imprint();r55.imprint();r65.imprint();
           r75.imprint();r85.imprint();r95.imprint();r105.imprint();r115.imprint();r125.imprint();

         }
        play.imprint();
        tplay.imprint();
        htp.imprint();
        thtp.imprint();
        hs.imprint();
        ths.imprint();
        exit.imprint();
        texit.imprint();
        endFrame();
    }

    bool isInside_menu(int x,int y,char ch)       //UPON A CLICK FROM THE USER, THIS FUNCTION CHECKS IF THE CLICK IS WITHIN ANY RECTANGLE
    {
        if(x>200 && x<400 && y<250 && y>150 && ch=='p')     //IF CLICK IS IN PLAY RECTANGLE
        {
            return true;
        }
        else if(x>200 && x<400 && y<350 && y>250&& ch=='h')    //IF CLICK IS IN HOW TO PLAY RECTANGLE
        {
            return true;
        }
        else if(x>200 && x<400 && y<450 && y>350 && ch=='g')   //IF CLICK IS IN HIGH SCORE RECTANGLE
        {
            return true;
        }
        else if(x>200 && x<400 && y<550 && y>450 && ch=='e')   //IF CLICK IS IN EXIT RECTANGLE
        {
            return true;
        }
        else
        {
            return false;
        }
    }

    void build_levelno()                            //This function builds the graphics for displaying the level numbers
    {
        beginFrame();
        clearall();                                 //CLEARING THE SCREEN TO DISPLAY THE LEVELS
        Text levelnum(300,40,"CHOOSE YOUR LEVEL");
        levelnum.imprint();
        Rectangle l1(130,265,60,60),
                  l2(200,265,60,60),
                  l3(270,265,60,60),
                  l4(340,265,60,60),
                  l5(410,265,60,60),
                  l6(130,335,60,60),
                  l7(200,335,60,60),
                  l8(270,335,60,60),
                  l9(340,335,60,60),
                  l10(410,335,60,60),
                  l11(130,405,60,60),
                  l12(200,405,60,60),
                  l13(270,405,60,60),
                  l14(340,405,60,60),
                  l15(410,405,60,60),
                  l16(130,475,60,60),
                  l17(200,475,60,60),
                  l18(270,475,60,60),
                  l19(340,475,60,60),
                  l20(410,475,60,60);

        Text  tl1(130,265,"Lev 1"),
              tl2(200,265,"Lev 2"),
              tl3(270,265,"Lev 3"),
              tl4(340,265,"Lev 4"),
              tl5(410,265,"Lev 5"),
              tl6(130,335,"Lev 6"),
              tl7(200,335,"Lev 7"),
              tl8(270,335,"Lev 8"),
              tl9(340,335,"Lev 9"),
              tl10(410,335,"Lev 10"),
              tl11(130,405,"Lev 11"),
              tl12(200,405,"Lev 12"),
              tl13(270,405,"Lev 13"),
              tl14(340,405,"Lev 14"),
              tl15(410,405,"Lev 15"),
              tl16(130,475,"Lev 16"),
              tl17(200,475,"Lev 17"),
              tl18(270,475,"Lev 18"),
              tl19(340,475,"Lev 19"),
              tl20(410,475,"Lev 20");

        l1.imprint();
        tl1.imprint();
        l2.imprint();
        tl2.imprint();
        l3.imprint();
        tl3.imprint();
        l4.imprint();
        tl4.imprint();
        l5.imprint();
        tl5.imprint();
        l6.imprint();
        tl6.imprint();
        l7.imprint();
        tl7.imprint();
        l8.imprint();
        tl8.imprint();
        l9.imprint();
        tl9.imprint();
        l10.imprint();
        tl10.imprint();

        l11.imprint();
        tl11.imprint();
        l12.imprint();
        tl12.imprint();
        l13.imprint();
        tl13.imprint();
        l14.imprint();
        tl14.imprint();
        l15.imprint();
        tl15.imprint();
        l16.imprint();
        tl16.imprint();
        l17.imprint();
        tl17.imprint();
        l18.imprint();
        tl18.imprint();
        l19.imprint();
        tl19.imprint();
        l20.imprint();
        tl20.imprint();
        endFrame();
    }

    bool isInside_level(int level,int xcoor,int ycoor)               //This function check is the click from the user is inside a level number rectangle
    {
        if(level==1 && xcoor>100 && xcoor<160 && ycoor>235 && ycoor<295)
        {
            return true;
        }
        else if(level==2 && xcoor>170 && xcoor<230  && ycoor>235 && ycoor<295)
        {
            return true;
        }
        else if(level==3 && xcoor>240 && xcoor<300 && ycoor>235 && ycoor<295)
        {
            return true;
        }
        else if(level==4 && xcoor>310 && xcoor<370 && ycoor>235 && ycoor<295)
        {
            return true;
        }
        else if(level==5 && xcoor>380 && xcoor<440 && ycoor>235 && ycoor<295)
        {
            return true;
        }
        else if(level==6 && xcoor>100 && xcoor<160 && ycoor>305 && ycoor<365)
        {
            return true;
        }
        else if(level==7 && xcoor>170 && xcoor<230 && ycoor>305 && ycoor<365)
        {
            return true;
        }
        else if(level==8 && xcoor>240 && xcoor<300 && ycoor>305 && ycoor<365)
        {
            return true;
        }
        else if(level==9 && xcoor>310 && xcoor<370 && ycoor>305 && ycoor<365)
        {
            return true;
        }
        else if(level==10 && xcoor>380 && xcoor<440 && ycoor>305 && ycoor<365)
        {
            return true;
        }
        else if(level==11 && xcoor>100 && xcoor<160 && ycoor>375 && ycoor<435)
        {
            return true;
        }
        else if(level==12 && xcoor>170 && xcoor<230  && ycoor>375 && ycoor<435)
        {
            return true;
        }
        else if(level==13 && xcoor>240 && xcoor<300 && ycoor>375 && ycoor<435)
        {
            return true;
        }
        else if(level==14 && xcoor>310 && xcoor<370 && ycoor>375 && ycoor<435)
        {
            return true;
        }
        else if(level==15 && xcoor>380 && xcoor<440 && ycoor>375 && ycoor<435)
        {
            return true;
        }
        else if(level==16 && xcoor>100 && xcoor<160 && ycoor>445 && ycoor<505)
        {
            return true;
        }
        else if(level==17 && xcoor>170 && xcoor<230 && ycoor>445 && ycoor<505)
        {
            return true;
        }
        else if(level==18 && xcoor>240 && xcoor<300 && ycoor>445 && ycoor<505)
        {
            return true;
        }
        else if(level==19 && xcoor>310 && xcoor<370 && ycoor>445 && ycoor<505)
        {
            return true;
        }
        else if(level==20 && xcoor>380 && xcoor<440 && ycoor>445 && ycoor<505)
        {
            return true;
        }
        else
        {
            return  false;
        }
    }

    void build_htplay()           //This function deals with building the graphics and algorithm of the how to play page.
    {
        //The how to play page is a booklet. THe user "turns" the pages and can go back to menu page any time.
        while(1)   //PAGE 1 STARTS HERE
        {
pg1:
            ;
            clearall();
            {
                //TO BUILD GRAPHICS FOR PAGE 1
                beginFrame();
                Text t1(300,30,"INSTRUCTIONS");
                t1.imprint();
                Text ta(300,80,"Clicking on the horizontal block on right side moves the block to the ");
                ta.imprint();// block to the right & clicking on the left side of the block makes it go left. ");
                Text ta1(300,130,"right & clicking on the left side of the block makes it go left. ");
                ta1.imprint();
                Text t23(300,222.5,"right click=>");
                t23.imprint();
                Rectangle r1(150,222.5,70,35);
                Rectangle r11(450,222.5,70,35);
                Rectangle r12(485,222.5,70,35);
                Rectangle r121(150,327.5,70,35);
                Text t231(300,327.5,"left click=>");
                t231.imprint();
                Rectangle r122(450,327.5,70,35);
                Rectangle r123(415,327.5,70,35);
                r121.setFill(true);
                r121.setColor(COLOR("red"));
                r121.imprint();
                r122.setFill(true);
                r122.setColor(COLOR(255,165,79));
                r122.imprint();
                r123.setFill(true);
                r123.setColor(COLOR("red"));
                r123.imprint();
                r1.setFill(true);
                r1.setColor(COLOR("red"));
                r1.imprint();
                r11.setFill(true);
                r11.setColor(COLOR(255,165,79));
                r11.imprint();
                r12.setFill(true);
                r12.setColor(COLOR("red"));
                r12.imprint();
                // Rectangle left(25,575,50,50);
                Rectangle right(575,575,50,50);
                right.imprint();
                Rectangle mainmenu(300,575,100,50);
                mainmenu.imprint();
                // Text lef(25,575,"<=");
                Text righ(575,575,"=>");
                righ.imprint();
                Text menu(300,575,"MENU");
                menu.imprint();
                endFrame();
            }
            XEvent next1;
            while(1)
            {
                nextEvent(next1);
                if(mouseButtonPressEvent(next1))
                {
                    xnext1=next1.xbutton.x;
                    ynext1=next1.xbutton.y;
                    if(xnext1>550 && xnext1<600 && ynext1>550 && ynext1<600)      //GO TO PAGE 2 FROM PAGE 1
                    {
                        while(1)     //PAGE 2 START HERE
                        {
pg2:
                            ;
                            clearall();
                            {
                                //TO BUILD GRAPHICS FOR PAGE 2
                                beginFrame();
                                Text t1(300,30,"INSTRUCTIONS");
                                t1.imprint();
                                Text tb(300,80,"Clicking on the vertical block on top side moves the block up");
                                tb.imprint();//& similarly clicking on it's bottom makes it go down.");
                                Text tb1(300,130,"& similarly clicking on it's bottom makes it go down.");
                                tb1.imprint();
                                Rectangle r2(150,232.5,35,70);
                                r2.setFill(true);
                                r2.setColor(COLOR("red"));
                                r2.imprint();
                                Rectangle r21(450,232.5,35,70);
                                r21.setFill(true);
                                r21.setColor(COLOR(255,165,79));
                                r21.imprint();
                                Rectangle r22(450,262.5,35,70);
                                r22.setFill(true);
                                r22.setColor(COLOR("red"));
                                r22.imprint();
                                Rectangle r211(150,382.5,35,70);
                                Rectangle r212(450,382.5,35,70);
                                Rectangle r213(450,347.5,35,70);
                                r211.setFill(true);
                                r212.setFill(true);
                                r213.setFill(true);
                                r211.setColor(COLOR("red"));
                                r211.imprint();
                                r212.setColor(COLOR(255,165,79));
                                r212.imprint();
                                r213.setColor(COLOR("red"));
                                r213.imprint();
                                Text t341(300,382.5,"top click=>");
                                t341.imprint();

                                Text t34(300,232.5,"bottom click=>");
                                t34.imprint();
                                Rectangle left(25,575,50,50);
                                left.imprint();
                                Rectangle right(575,575,50,50);
                                right.imprint();
                                Rectangle mainmenu(300,575,100,50);
                                mainmenu.imprint();
                                Text lef(25,575,"<=");
                                lef.imprint();
                                Text righ(575,575,"=>");
                                righ.imprint();
                                Text menu(300,575,"MENU");
                                menu.imprint();
                                endFrame();
                            }
                            XEvent next2;
                            while(1)
                            {
                                nextEvent(next2);
                                if(mouseButtonPressEvent(next2))
                                {
                                    xnext2=next2.xbutton.x;
                                    ynext2=next2.xbutton.y;
                                    if(xnext2>550 && xnext2<600 && ynext2>550 && ynext2<600)   //GO TO PAGE 3 FROM PAGE 2
                                    {
                                        while(1)  //PAGE 3 START HERE
                                        {
                                            clearall();
                                            {
                                                //TO BUILD THE GRAPHICS FOR PAGE 3
                                                beginFrame();
                                                Text t4(300,80,"Clicking on the middle part of 1x3 and 3x1 leaves the position of block unchanged.");
                                                t4.imprint();
                                                Text t5(300,180,"Goal of this game is to help the red block escape the grid ");
                                                t5.imprint();//by moving the other blocks out of the way appropriately.");
                                                Text t6(300,220,"by moving the other blocks out of the way appropriately.");
                                                t6.imprint();
                                                Text t7(300,320,"No two blocks can overlap each other or escape the grid.");
                                                t7.imprint();
                                                Rectangle left(25,575,50,50);
                                                left.imprint();
                                                Rectangle mainmenu(300,575,100,50);
                                                mainmenu.imprint();
                                                Text lef(25,575,"<=");
                                                lef.imprint();
                                                Text menu(300,575,"MENU");
                                                menu.imprint();
                                                endFrame();
                                            }

                                            XEvent next3;
                                            while(1)
                                            {
                                                nextEvent(next3);
                                                if(mouseButtonPressEvent(next3))
                                                {
                                                    xnext3=next3.xbutton.x;
                                                    ynext3=next3.xbutton.y;
                                                    if(xnext3>0 && xnext3<50 && ynext3>550 && ynext3<600)    //TO GO TO PAGE 2 FROM PAGE 3
                                                    {
                                                        goto pg2;
                                                    }
                                                    if(xnext3>250 && xnext3<350 && ynext3>550 && ynext3<600)  //TO GO TO MENU PAGE FOM PAGE 3
                                                    {
                                                        goto end_it;
                                                    }
                                                }
                                            }
                                            break;
                                        }     //  while(1) if page 3 end here

                                    }
                                    // page 3 end here   takes coordinates from page 2

                                    if(xnext2>0 && xnext2<50 && ynext2>550 && ynext2<600)      //TO GO TO PAGE 1 FROM PAGE 2
                                    {
                                        goto pg1;
                                    }
                                    if(xnext2>250 && xnext2<350 && ynext2>550 && ynext2<600)   //TO GO TO MENU PAGE FROM PAGE 2
                                    {
                                        goto end_it;    //break from the while(1) at line 658
                                    }
                                }
                            }

                            break;
                        }     //while(1) of page 2 end here
                    }   //Page 2 end here
                    if(xnext1>250 && xnext1<350 && ynext1>550 && ynext1<600)    //GO TO MENU FROM PAGE1
                    {
                        break;
                    }
                }

            }

            break;
        }
    end_it:
        ;
    }

    void build_highscore()        //This function builds the graphics for the high score and also takes the input from the updated high score file
    {                             //and displays the high score for each level on the canvas.
        int i;

        clearall();
        beginFrame();
        Rectangle peach(300,300,600,600);
        peach.setFill(1);
        peach.setColor(COLOR(237,253,161)), peach.imprint();
        Rectangle black(300,575,100,50);
        black.setFill(1);
        black.setColor(COLOR("black"));
        black.imprint();
        Text lev1(100,120,"Level 1");
        Text lev2(200,120,"Level 2");
        Text lev3(300,120,"Level 3");
        Text lev4(400,120,"Level 4");
        Text lev5(500,120,"Level 5");
        Text lev6(100,240,"Level 6");
        Text lev7(200,240,"Level 7");
        Text lev8(300,240,"Level 8");
        Text lev9(400,240,"Level 9");
        Text lev10(500,240,"Level 10");
        Text lev11(100,360,"Level 11");
        Text lev12(200,360,"Level 12");
        Text lev13(300,360,"Level 13");
        Text lev14(400,360,"Level 14");
        Text lev15(500,360,"Level 15");
        Text lev16(100,480,"Level 16");
        Text lev17(200,480,"Level 17");
        Text lev18(300,480,"Level 18");
        Text lev19(400,480,"Level 19");
        Text lev20(500,480,"Level 20");

        lev1.imprint();
        lev2.imprint();
        lev3.imprint();
        lev4.imprint();
        lev5.imprint();
        lev6.imprint();
        lev7.imprint();
        lev8.imprint();
        lev9.imprint();
        lev10.imprint();
        lev11.imprint();
        lev12.imprint();
        lev13.imprint();
        lev14.imprint();
        lev15.imprint();
        lev16.imprint();
        lev17.imprint();
        lev18.imprint();
        lev19.imprint();
        lev20.imprint();

        Text mainmenu1(300,575,"Go Back");
        mainmenu1.imprint();
        Rectangle mainmenu(300,575,100,50);
        mainmenu.imprint();

        endFrame();
        beginFrame();
        ifstream txt("high score.txt");
        //string data;
        for(i=0; i<20; i++)
        {
            string ch;
            txt>>ch;
            if(ch=="1000")
            {
                Text put(100*((i%5)+1),(120*((i/5)+1))+30,"Incomplete");
                put.imprint();
            }
            else
            {
                Text put(100*((i%5)+1),(120*((i/5)+1))+30,ch);
                put.imprint();
            }
        }
        endFrame();
    }

};

class build_level_comp : public unblkme //This class was made to combines all the function of unblock me class and the Canvas interface
{

public:
    unblkme levelno;
    int i,j;
    int xplay,yplay;

    void build_level(int i)             //Recognizes the events on the Canvas prompted by the user and runs the level
    {
        levelno.init_level(i);
        clearall();
        levelno.buildlevel();
        XEvent play;
        while(1)
        {
            nextEvent(play);
            if(mouseButtonPressEvent(play))
            {
                xplay=play.xbutton.x;
                yplay=play.xbutton.y;
                i=(yplay-90)/70;
                j=(xplay-90)/70;
                if(xplay>90 && yplay>90)
                {
                    goto A;
                }
                else if(i==6 && j==0)
                {
                    break;
                }
                else if(i==0 && j==0)
                {
                    break;
                }
A:
                ;
                levelno.buildlevel_after(i,j);    //Builds the level after the user has clicked
                if(levelno.levela[2][5]==3 && levelno.levelb[2][5]=='r')    //Shows the user if the user has won the game
                {
                    Text winwin(300,20,"!!WINNER WINNER, CHICKEN DINNER!!");
                    wait(1.5);
                    break;
                }
            }
        }

    }
};

main_program
{
    int score;
    initCanvas("Game",600,600);   //Initializes the Canvas
    menu_level obj;               //Declares an object of menu_level class to run the menu and the level number page.
    while(1)
    {
        obj.build_menu();
        XEvent click_menu;
        nextEvent(click_menu);
        if(mouseButtonPressEvent(click_menu))
        {
            int xmenu=click_menu.xbutton.x;
            int ymenu=click_menu.xbutton.y;

            if(obj.isInside_menu(xmenu,ymenu,'p'))    //If the user has click on "PLAY"
            {
                while(1)
                {
                    obj.build_levelno();
                    XEvent level;
                    nextEvent(level);
                    if(mouseButtonPressEvent(level))
                    {
                        nextEvent(level);
                        int xlevel=level.xbutton.x;
                        int ylevel=level.xbutton.y;
                                                                     //THESE COORDINATES ARE CHECKED AND THEN BUILDS THE CORRESPONDING LEVEL ON WHICH THE USER CLICKED
                        if(obj.isInside_level(1,xlevel,ylevel))     //LEVEL NUMBER, X COORDINATE, Y COORDINATE  //LEVEL 1
                        {
                            build_level_comp level1;
                            level1.build_level(1);
                            if(level1.xplay>20 && level1.xplay<70 && level1.yplay>530 && level1.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level1.i==0 && level1.j==0)        //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level1.levelno.levela[2][5]==3 && level1.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level1.levelno.no_of_steps;
                                update_hs(1,score);
                                wait(1);
                                goto a1;
                            }

                        }
                        else if(obj.isInside_level(2,xlevel,ylevel))
                        {
a1:
                            ;
                            build_level_comp level2;
                            level2.build_level(2);
                            if(level2.xplay>20 && level2.xplay<70 && level2.yplay>530 && level2.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level2.i==0 && level2.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level2.levelno.levela[2][5]==3 && level2.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level2.levelno.no_of_steps;
                                update_hs(2,score);
                                wait(1);
                                goto a2;
                            }
                        }
                        else if(obj.isInside_level(3,xlevel,ylevel))
                        {
a2:
                            ;
                            build_level_comp level3;
                            level3.build_level(3);
                            if(level3.xplay>20 && level3.xplay<70 && level3.yplay>530 && level3.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level3.i==0 && level3.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level3.levelno.levela[2][5]==3 && level3.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level3.levelno.no_of_steps;
                                update_hs(3,score);
                                wait(1);
                                goto a3;
                            }
                        }
                        else if(obj.isInside_level(4,xlevel,ylevel))
                        {
a3:
                            ;
                            build_level_comp level4;
                            level4.build_level(4);
                            if(level4.xplay>20 && level4.xplay<70 && level4.yplay>530 && level4.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level4.i==0 && level4.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level4.levelno.levela[2][5]==3 && level4.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level4.levelno.no_of_steps;
                                update_hs(4,score);
                                wait(1);
                                goto a4;
                            }
                        }
                        else if(obj.isInside_level(5,xlevel,ylevel))
                        {
a4:
                            ;
                            build_level_comp level5;
                            level5.build_level(5);
                            if(level5.xplay>20 && level5.xplay<70 && level5.yplay>530 && level5.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level5.i==0 && level5.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level5.levelno.levela[2][5]==3 && level5.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level5.levelno.no_of_steps;
                                update_hs(5,score);
                                wait(1);
                                goto a5;
                            }
                        }
                        else if(obj.isInside_level(6,xlevel,ylevel))
                        {
a5:
                            ;
                            build_level_comp level6;
                            level6.build_level(6);
                            if(level6.xplay>20 && level6.xplay<70 && level6.yplay>530 && level6.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level6.i==0 && level6.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level6.levelno.levela[2][5]==3 && level6.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level6.levelno.no_of_steps;
                                update_hs(6,score);
                                wait(1);
                                goto a6;
                            }
                        }
                        else if(obj.isInside_level(7,xlevel,ylevel))
                        {
a6:
                            ;
                            build_level_comp level7;
                            level7.build_level(7);
                            if(level7.xplay>20 && level7.xplay<70 && level7.yplay>530 && level7.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level7.i==0 && level7.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level7.levelno.levela[2][5]==3 && level7.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level7.levelno.no_of_steps;
                                update_hs(7,score);
                                wait(1);
                                goto a7;
                            }
                        }
                        else if(obj.isInside_level(8,xlevel,ylevel))
                        {
a7:
                            ;
                            build_level_comp level8;
                            level8.build_level(8);
                            if(level8.xplay>20 && level8.xplay<70 && level8.yplay>530 && level8.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level8.i==0 && level8.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level8.levelno.levela[2][5]==3 && level8.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level8.levelno.no_of_steps;
                                update_hs(8,score);
                                wait(1);
                                goto a8;
                            }
                        }
                        else if(obj.isInside_level(9,xlevel,ylevel))
                        {
a8:
                            ;
                            build_level_comp level9;
                            level9.build_level(9);
                            if(level9.xplay>20 && level9.xplay<70 && level9.yplay>530 && level9.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level9.i==0 && level9.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level9.levelno.levela[2][5]==3 && level9.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level9.levelno.no_of_steps;
                                update_hs(9,score);
                                wait(1);
                                goto a9;
                            }
                        }
                        else if(obj.isInside_level(10,xlevel,ylevel))
                        {
a9:
                            ;
                            build_level_comp level10;
                            level10.build_level(10);
                            if(level10.xplay>20 && level10.xplay<70 && level10.yplay>530 && level10.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level10.i==0 && level10.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level10.levelno.levela[2][5]==3 && level10.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level10.levelno.no_of_steps;
                                update_hs(10,score);
                                wait(1);
                                goto a10;
                            }
                        }
                        else if(obj.isInside_level(11,xlevel,ylevel))
                        {
a10:
                            ;
                            build_level_comp level11;
                            level11.build_level(11);
                            if(level11.xplay>20 && level11.xplay<70 && level11.yplay>530 && level11.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level11.i==0 && level11.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level11.levelno.levela[2][5]==3 && level11.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level11.levelno.no_of_steps;
                                update_hs(11,score);
                                wait(1);
                                goto a11;
                            }

                        }
                        else if(obj.isInside_level(12,xlevel,ylevel))
                        {
a11:
                            ;
                            build_level_comp level12;
                            level12.build_level(12);
                            if(level12.xplay>20 && level12.xplay<70 && level12.yplay>530 && level12.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level12.i==0 && level12.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level12.levelno.levela[2][5]==3 && level12.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level12.levelno.no_of_steps;
                                update_hs(12,score);
                                wait(1);
                                goto a12;
                            }
                        }
                        else if(obj.isInside_level(13,xlevel,ylevel))
                        {
a12:
                            ;
                            build_level_comp level13;
                            level13.build_level(13);
                            if(level13.xplay>20 && level13.xplay<70 && level13.yplay>530 && level13.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level13.i==0 && level13.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level13.levelno.levela[2][5]==3 && level13.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level13.levelno.no_of_steps;
                                update_hs(13,score);
                                wait(1);
                                goto a13;
                            }
                        }
                        else if(obj.isInside_level(14,xlevel,ylevel))
                        {
a13:
                            ;
                            build_level_comp level14;
                            level14.build_level(14);
                            if(level14.xplay>20 && level14.xplay<70 && level14.yplay>530 && level14.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level14.i==0 && level14.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level14.levelno.levela[2][5]==3 && level14.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level14.levelno.no_of_steps;
                                update_hs(14,score);
                                wait(1);
                                goto a14;
                            }
                        }
                        else if(obj.isInside_level(15,xlevel,ylevel))
                        {
a14:
                            ;
                            build_level_comp level15;
                            level15.build_level(15);
                            if(level15.xplay>20 && level15.xplay<70 && level15.yplay>530 && level15.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level15.i==0 && level15.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level15.levelno.levela[2][5]==3 && level15.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level15.levelno.no_of_steps;
                                update_hs(15,score);
                                wait(1);
                                goto a15;
                            }
                        }
                        else if(obj.isInside_level(16,xlevel,ylevel))
                        {
a15:
                            ;
                            build_level_comp level16;
                            level16.build_level(16);
                            if(level16.xplay>20 && level16.xplay<70 && level16.yplay>530 && level16.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level16.i==0 && level16.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level16.levelno.levela[2][5]==3 && level16.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level16.levelno.no_of_steps;
                                update_hs(16,score);
                                wait(1);
                                goto a16;
                            }
                        }
                        else if(obj.isInside_level(17,xlevel,ylevel))
                        {
a16:
                            ;
                            build_level_comp level17;
                            level17.build_level(17);
                            if(level17.xplay>20 && level17.xplay<70 && level17.yplay>530 && level17.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level17.i==0 && level17.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level17.levelno.levela[2][5]==3 && level17.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level17.levelno.no_of_steps;
                                update_hs(17,score);
                                wait(1);
                                goto a17;
                            }
                        }
                        else if(obj.isInside_level(18,xlevel,ylevel))
                        {
a17:
                            ;
                            build_level_comp level18;
                            level18.build_level(18);
                            if(level18.xplay>20 && level18.xplay<70 && level18.yplay>530 && level18.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level18.i==0 && level18.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level18.levelno.levela[2][5]==3 && level18.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level18.levelno.no_of_steps;
                                update_hs(18,score);
                                wait(1);
                                goto a18;
                            }
                        }
                        else if(obj.isInside_level(19,xlevel,ylevel))
                        {
a18:
                            ;
                            build_level_comp level19;
                            level19.build_level(19);
                            if(level19.xplay>20 && level19.xplay<70 && level19.yplay>530 && level19.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level19.i==0 && level19.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level19.levelno.levela[2][5]==3 && level19.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level19.levelno.no_of_steps;
                                update_hs(19,score);
                                wait(1);
                                goto a19;
                            }
                        }
                        else if(obj.isInside_level(20,xlevel,ylevel))
                        {
a19:
                            ;
                            build_level_comp level20;
                            level20.build_level(20);
                            if(level20.xplay>20 && level20.xplay<70 && level20.yplay>530 && level20.yplay<580)  //GOES TO LEVEL NUMBER PAGE
                            {
                                continue;
                            }
                            else if(level20.i==0 && level20.j==0)     //GOES TO MENU PAGE
                            {
                                break;
                            }
                            if(level20.levelno.levela[2][5]==3 && level20.levelno.levelb[2][5]=='r')   //IF USER FINIHSED THE LEVEL, UPDATES THE HIGHSCORE PAGE
                            {                                                                        //AND SHOWS THE NEXT LEVEL
                                score=level20.levelno.no_of_steps;
                                update_hs(20,score);
                                wait(1);
                                break;
                            }
                        }

                    }  //CHECK IF A MOUSE BUTTON WAS PRESSED OR NOT IN THE LEVEL PAGE

                }

            }  //THIS CURLY BARCE IS THE END OF LEVEL....IE IF YOU CLICK IN THE PLAY RECT IN MENU, THIS IS THE COREESPONDING IF LOOP
            else if(obj.isInside_menu(xmenu,ymenu,'h'))    //If the user has click on "HOT TO PLAY"
            {
                obj.build_htplay();
                if(obj.xnext1>250 && obj.xnext1<350 && obj.ynext1>550 && obj.ynext1<600)   //THESE CONDITIONS ENSURES THAT IF THE USER CLICKED ON "MENU",
                {                                                                          //GOES TO MENU PAGE
                    continue;
                }
                else if(obj.xnext2>250 && obj.xnext2<350 && obj.ynext2>550 && obj.ynext2<600)
                {
                    continue;
                }
                else if(obj.xnext3>250 && obj.xnext3<350 && obj.ynext3>550 && obj.ynext3<600)
                {
                    continue;
                }
                wait(2);

            }
            else if(obj.isInside_menu(xmenu,ymenu,'e'))    //If the user has click on "EXIT"
            {
                break;             //EXITS THE CANVAS. GAME ENDS
            }
            else if(obj.isInside_menu(xmenu,ymenu,'g'))    //If the user has click on "HIGH SCORE"
            {
                obj.build_highscore();
                XEvent goback;
                while(1)
                {
                    nextEvent(goback);
                    if(mouseButtonPressEvent(goback))
                    {
                        int x=goback.xbutton.x;
                        int y=goback.xbutton.y;
                        if(x>250 && x<350 && y>550 && y<600)    //IN THE HIGH SCORE PAGE, IF THE USER HAS CLICKED ON "MENU", GO TO MENU PAGE
                        {
                            break;
                        }
                    }
                }

            }

        }  //CHECK IF A MOUSE BUTTON WAS PRESSED OR NOT IN THE MENU

    }

}
