#Random Boxes

I wanted to split the page into a [number of segments](https://benjaminfox1.github.io/random_boxes/)  and create a number of squares randomly within them from key presses. Idea of spawning enemy characters for a game against the blue player box.

<details><summary>Code Below</summary>
<p>

```javascript
//Grid where we have to place our grid over another grid to win
var gameState;
var newState;
var spawnPosX1;
var spawnPosY1;
var spawnPosX2;
var spawnPosY2;
var spawnPosX3;
var spawnPosY3;

var enemyObjects;

function setup() {
  createCanvas(800, 800);
  gameState=0;
  newState=0;
  enemyObject=0;
}

function draw() {
  background(200);

   //define myobject
   let myObject = 
   {
     xPos:0,
     yPos:0,
     sizeX: width/10,
     sizeY: height/10,
     colour: 255
   };
   
  stroke(100);
  strokeWeight(1);

  if (newState==0)
  {
    noStroke;
    spawnPosX1=int(random(0,10));//creates a random number between 0 and 10
    spawnPosY1=int(random(0,10));
    fill(0,0,255,100);
    textSize(width/25);
    text("Press 1 to start, 2 to quit, \n 3 to generate new squares",width/8,height/2);
  }

  if (newState==1)
  {
     //draw lines on the canvas
     for (let i=0;i<10;i++)
     {
        strokeWeight(4);
        stroke(100,0,0);
        line(width/10*i,0,width/10*i,height);
        stroke(0,0,25*i);
        line(0,height/10*i,width,height/10*i)
      }
  
    //draw myObject
    noStroke;
    fill(0,0,myObject.colour,100);
    
    rect(
      myObject.xPos,
      myObject.yPos,
      myObject.sizeX,
      myObject.sizeY);
   
    //create enemy rectangles on the right edge in one of 10 locations (ie the squares)
    fill(255,0,0);

    if (enemyObject<3)
    {
      noStroke();
      fill(200,0,0);
      rect(
      myObject.sizeX*(spawnPosX1),
      myObject.sizeY*(spawnPosY1),
      myObject.sizeX,
      myObject.sizeY,
      )

      rect(
        myObject.sizeX*(spawnPosX2),
        myObject.sizeY*(spawnPosY2),
        myObject.sizeX,
        myObject.sizeY,
        )

      rect(
        myObject.sizeX*(spawnPosX3),
        myObject.sizeY*(spawnPosY3),
        myObject.sizeX,
        myObject.sizeY,
        )
    };
  }

  spawnPosX1=spawnPosX1-0.02;
  spawnPosX2=spawnPosX2-0.02;
  spawnPosX3=spawnPosX3-0.02;

};

function keyTyped ()
{
  if (key==='1'){
    newState=1;
    gameState=1;
  } else if (key==='2')
  {
    newState=0;
    gameState=0;
  } else if (key==='3')
  {
    spawnPosX1=int(random(0,10));//creates a random number between 0 and 10
    spawnPosY1=int(random(0,10));
    spawnPosX2=int(random(0,10));//creates a random number between 0 and 10
    spawnPosY2=int(random(0,10));
    spawnPosX3=int(random(0,10));
    spawnPosY3=int(random(0,10));
  } ;
}

  ```
</p>
</details>
