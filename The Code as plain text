//Mark Chen
//June 2018
//This program is a 2 player "super tic tac toe " game,
//meaning there are 9 smaller games inside of one large tic tac toe game.
//To win, one must win the big tic tac toe game, by claiming 3 wins of the smaller games in a manner that results in a win for normal gameplay.

//Print rules to players
println("Welcome to TIC TAC TOE TAC TIC\nThis is a 2 player game. Find a foe!\nThere are 9 smaller normal tic tac toe games inside of one large game.\nTo win, one must win the big tic tac toe game, by claiming 3 wins of the smaller games in a manner that results in a win on the large game.\nGood luck and have fun!\n");


//Global variables

//For mouse animation
var mouseMoveX= 0.0;
var mouseMoveY = 0.0;
var followSpeed = 0.25;

//Counts if it is X or O's turn
var xoCounter = 0;

//Global index tracker for arrays
var tempX;
var tempY;

//Game over switch
var gameOver = false;

//Big array for big 3 by 3 game
var gridLarge = [   ["","",""],
                    ["","",""],
                    ["","",""]  ];

//Grid array 0 to 8 (9 by 9) --- the 9 smaller games
var gridArray = [   ["","","","","","","","",""],
                    ["","","","","","","","",""],
                    ["","","","","","","","",""],
                    ["","","","","","","","",""],
                    ["","","","","","","","",""],
                    ["","","","","","","","",""],
                    ["","","","","","","","",""],
                    ["","","","","","","","",""],
                    ["","","","","","","","",""]   ];

//This function will see if the game is a tie everytime the mouse is pressed
var checkTie = function(){
    //Only if the game is not a win, see if it is a tie yet
    if (!gameOver){
    
        //Find tie game on the big grid and the small grid
        var tie = true;
        var countEmpty;
        countEmpty = 1;
        //Search in all elements for an empty spot
        for (var a = 0;a<=8;a++){
            for (var b = 0;b<=8;b++){
                //If room for moves, no tie exists
                if (gridArray[a][b]===""){
                    tie = false;
                    countEmpty++;
                }
            }
        }
        
        //println(countEmpty);
        
        //Search in 3 by 3 for any signs of a move left or a win
        for (var a = 0;a<=2;a++){
            for (var b = 0;b<=2;b++){
                //If room for moves or game was closed, no tie exists
                if (gridLarge[a][b]==="" || gridLarge ==="F"){
                    tie = false;
                }
            }
        }
        
        //If the number of empty cells is not the initialized value, it is a tie
        if (countEmpty===1){
            tie = true;
        }
        
        //If the game has ended, and is a tie, tell user(s) it is a tie + gameover.
        if (tie){
            println("It is a tie game.");
            gameOver = true;
            println(" <===== To restart game, press 'restart'.");
        }
    }
};


//See if the large 3 by 3 game is won
var checkBigWin = function(){

    //Let a variable represent the symbol X or O
    var Z = "O";
    //Change letter if needed
    if (xoCounter%2===0){
        Z = "X";
    }
    
    /*
    println(gridLarge[0]);
    println(gridLarge[1]);
    println(gridLarge[2]);
    */
    
    //Check to see if there is a win (3 by 3)
    if (
(gridLarge[0][0] === Z && gridLarge[0][1] === Z && gridLarge[0][2] === Z)||
(gridLarge[1][0] === Z && gridLarge[1][1] === Z && gridLarge[1][2] === Z)||
(gridLarge[2][0] === Z && gridLarge[2][1] === Z && gridLarge[2][2] === Z)||
(gridLarge[0][0] === Z && gridLarge[1][0] === Z && gridLarge[2][0] === Z)||
(gridLarge[0][1] === Z && gridLarge[1][1] === Z && gridLarge[2][1] === Z)||
(gridLarge[0][2] === Z && gridLarge[1][2] === Z && gridLarge[2][2] === Z)||
(gridLarge[0][0] === Z && gridLarge[1][1] === Z && gridLarge[2][2] === Z)||
(gridLarge[0][2] === Z && gridLarge[1][1] === Z && gridLarge[2][0] === Z))
    {   
        //If a win exists, fill board - both big and small, so no moves can be made
        //Fill big array, replace empty elements with "F"
        for (var a = 0;a<=8;a++){
            for (var b = 0;b<=8;b++){
                if (gridArray[a][b]===""){
                    gridArray[a][b]="F";
                }
            }
        }
        //Fill small array, replace empty elements with "F"
        for (var a = 0;a<=2;a++){
            for (var b = 0;b<=2;b++){
                if (gridLarge[a][b]===""){
                    gridLarge[a][b]="F";
                }
            }
        }
    
        //Display congrats and game over
        println("Game Over - Player " + Z + " wins.");
        gameOver = true;
        println(" <===== To restart game, press 'restart'.");
    }
};


//See if win exists
var checkWin = function(){
    
    //Translate clicked area into top left element of each small 3 by 3 grid
    var X = tempX - (tempX%3);
    var Y = tempY - (tempY%3);
    var Z = "O";
    //Change letter if needed
    if (xoCounter%2===0){
        Z = "X";
    }
    
    //println(X);
    //println(Y);
    
    //If a win exists in a small grid, write it to the array
    if (
(gridArray[X][Y] === Z && gridArray[X][Y+1] === Z && gridArray[X][Y+2] === Z)||
(gridArray[X+1][Y] === Z && gridArray[X+1][Y+1] === Z && gridArray[X+1][Y+2] === Z)||
(gridArray[X+2][Y] === Z && gridArray[X+2][Y+1] === Z && gridArray[X+2][Y+2] === Z)||
(gridArray[X][Y] === Z && gridArray[X+1][Y] === Z && gridArray[X+2][Y] === Z)||
(gridArray[X][Y+1] === Z && gridArray[X+1][Y+1] === Z && gridArray[X+2][Y+1] === Z)||
(gridArray[X][Y+2] === Z && gridArray[X+1][Y+2] === Z && gridArray[X+2][Y+2] === Z)||
(gridArray[X][Y] === Z && gridArray[X+1][Y+1] === Z && gridArray[X+2][Y+2] === Z)||
(gridArray[X][Y+2] === Z && gridArray[X+1][Y+1] === Z && gridArray[X+2][Y] === Z))
    {
        
        //Add win to the large array
        var newX = Math.floor(X/3);
        var newY = Math.floor(Y/3);
        gridLarge[newX][newY] = Z;
        
        //Debugging
        //println("win");
        //println(gridLarge[0]);
        //println(gridLarge[1]);
        //println(gridLarge[2]);
        
        //Fill gaps after a 3 by 3 is won
        for (var a = 0;a<=2;a++){
            for (var b = 0;b<=2;b++){
                if (gridArray[a+X][b+Y]===""){
                    gridArray[a+X][b+Y]="F";
                }
            }
        }
    //Only after a smaller win, see if the big win exists
    checkBigWin();
    }
};


//Rounds all inputs (mouse positions) to nearest centre of square in grid
//Takes in mouseX or mouseY
//Returns rounded coordinates (centred to nearest square)
var roundNearestSquare = function(x) {
    //If in grid, otherwise gnore
    if (x>20 && x<380){
        //Round to square
        if (x%40 <= 20) {return x - (x%40);}
        else if (x%40 > 20) {return x + (40 - (x%40));}
    }
};


/*Takes the rounded square coordinates from grid and converts into respective element on array
Returns the coordinates in array for the clicked position
*/
var gridIndex = function(x,y){
    var intx = (x-20)/40;
    var inty = (y-20)/40;
    for (var a=0; a<=9;a++){
        var b = a-1;
        //Confirm element dimensions
        if (intx<=a && intx>b){intx = a;}
        if (inty<=a && inty>b){inty = a;}
    }
    var cPair = [inty, intx];
    return cPair;
};

//Draws the shapes where clicked
//Takes the parameters of the mouse position
//Draws respective symbol to middle of a aquare
var drawSymbol = function(x,y){
    
    //Only draws if square is empty, continuing until the player makes a legal move
    if (gridArray[gridIndex(x,y)[0]-1][gridIndex(x,y)[1]-1] === ""){

        //Decide what shape to draw and where to draw
        if (xoCounter%2===1){
            ellipse(roundNearestSquare(x),roundNearestSquare(y),30,30);
        } else {
            line(roundNearestSquare(x)-10,roundNearestSquare(y)-10,roundNearestSquare(x)+10,roundNearestSquare(y)+10);
        line(roundNearestSquare(x)+10,roundNearestSquare(y)-10,roundNearestSquare(x)-10,roundNearestSquare(y)+10);
        }
        
        //Writes symbol to array for storage
        if (xoCounter%2===1){
            gridArray[gridIndex(x,y)[0]-1][gridIndex(x,y)[1]-1] = "O";
        } else {
            gridArray[gridIndex(x,y)[0]-1][gridIndex(x,y)[1]-1] = "X";
        }
        
        //Store for later use and calculations
        tempX = gridIndex(x,y)[0]-1;
        tempY = gridIndex(x,y)[1]-1;
    } else {
        //If illegal move is made --- one has to keep playing legally
        println("Not allowed.");
        xoCounter+=1;
    }
    //See if a win exists after a move is made
    checkWin();
    checkTie();//work
};

var run = false;
var gameSize = 120;
draw = function() { 
    background(250);
    noFill();
  
  //Draws the grid into 9 smaller tic tac toe games
    for (var x=20;x<=380;x+=40){
        if (x===140 || x===260){
            strokeWeight(5);
        } else {
            strokeWeight(1);
        }
    line(20,x,380,x);
    line(x,380,x,20);
    }
    
    //When the mouse is clicked in range of the game, the exact mouse position is given to the actual draw function for the X and O's.
    if (run === true){
        //Next person's turn each click
        xoCounter++;
        //If in range, play, otherwise wait until a legal move is made
        if (mouseX>20 && mouseY>20 && mouseX<380 && mouseY<380){
            drawSymbol(mouseX,mouseY);
        } else {
            println("Play on grid plz.");
            xoCounter+=1;
        }
        //Turn off run to only run once until the mouse is clicked again.
        run = false;
    }
    
    //For all elements in play, if it holds a value, display respective shape
    for (var a = 0; a<=8; a++){
        //println(gridArray[a]);
        for (var b = 0; b<=8; b++){
            if (gridArray[a][b] ==="X"){
                line((b+1)*40-10,(a+1)*40-10,(b+1)*40+10,(a+1)*40+10);
                line((b+1)*40-10,(a+1)*40+10,(b+1)*40+10,(a+1)*40-10);
            } else if (gridArray[a][b] ==="O") {
                ellipse((b+1)*40,(a+1)*40,30,30);
            }
        }
    }
    //work
    //For any wins in a smaller game, print a larger shape in respective win area
    for (var a = 0; a<=2; a++){
        for (var b = 0; b<=2; b++){
            strokeWeight(3);
            if (gridLarge[a][b] ==="X"){
                var newX = a;
                var newY = b;
                line((newY)*120+40,(newX)*120+40,(newY)*120+120,(newX)*120+120);
                line((newY)*120+40,(newX)*120+120,(newY)*120+120,(newX)*120+40);
            } else if (gridLarge[a][b] ==="O") {
                var newX = a;
                var newY = b;
                ellipse((newY)*120+80,(newX)*120+80,100,100);
            }
            strokeWeight(1);
        }
    }
    
    //If the game is done
    if (gameOver){
        if (gameSize<=2){
            gameSize = 0;
        }
        textSize(gameSize);
        var f = createFont("kristen itc");
        fill(0);
        textFont(f);
        strokeWeight(15);
        
        text("Game Over",20,200+(gameSize/2));
        gameSize-=1.5;
    }
    noFill();
    strokeWeight(1);
    
    
    //From here to the end of the draw function, because of this cool effect,
    //I rearranged 80% of my code into a draw function
    
    //For turn based mouse following thingy
    var goToX = mouseX;
    var dx = goToX - mouseMoveX;
    var goToY = mouseY;
    var dy = goToY - mouseMoveY;
    //Move the shape towards mouse
    mouseMoveY += dy * followSpeed;
    mouseMoveX+= dx * followSpeed;
    
    //Decided if shape is a X or O
    if (xoCounter%2===0){
        stroke(122, 149, 230);
        strokeWeight(2);
        ellipse(mouseMoveX, mouseMoveY, 30, 30);
    } else {
        stroke(255, 43, 43);
        line(mouseMoveX-10, mouseMoveY-10,mouseMoveX+10, mouseMoveY+10);
        line(mouseMoveX-10, mouseMoveY+10,mouseMoveX+10, mouseMoveY-10);
    }
    
    stroke(0);
    strokeWeight(0);
};

//Whenever the mouse is clicked, run the drawing/main function
var mouseClicked = function(){
    run = true;
};
