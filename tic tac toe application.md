#  									***tic tac toe application***

# ***//1 HTML CODE***

# <!DOCTYPE html>

# <html lang="en">

# <head>

#     <meta charset="UTF-8">

#     <meta name="viewport" content="width=device-width, initial-scale=1.0">

#     <title>tic tac toe </title>

#     <link rel="stylesheet" href="tic.css">

# </head>

# <body>

#     <main>

#         <H1>*Tic Tac Toe*</H1>

#         <div class="container">

#             <div class="game">

#                 <div class="draw-container hide">

#                     <p id="draw-game">Draw</p>

#                 </div>

#                 <div class="msg-container hide">

#                     <p id="msg"></p>

#                 </div>

#                 <button class="box"></button>

#                 <button class="box"></button>

#                 <button class="box"></button>

#                 <button class="box"></button>

#                 <button class="box"></button>

#                 <button class="box"></button>

#                 <button class="box"></button>

#                 <button class="box"></button>

#                 <button class="box"></button>

#             </div>

#         </div>

#         <div Align="center">

#             <button id="reset">*Reset Game*</button>

#             <button id="new\\\\\\\_game">*New Game*</button>

#         </div>

#     </main>

#     <script src="tic.js"></script>

#  

# </body>

# </html>

# ***2= CSS CODE***

# \*{

#     margin: 0;

#     padding: 0;

# 

# }

# body{

# 

#     background: rgb(169, 127, 213);

#     justify-content: center;

#     align-items: center;

#     display: flex;

#     /\* flex-direction: column;  \*/

# }

# h1 {

#     text-align: center;

#     font-size: xxx-large;

#     font-family: cursive

# }

# .container{

#     height: 70vh;

#     display: flex;

#     flex-wrap: wrap;

#     justify-content: center;

#     align-items: center;

# }

# .game{

#     height: 60vmin;

#     width: 60vmin;

#     justify-content: center;

#     display: flex;

#     flex-wrap: wrap;

#     align-items: center;

#     gap: 2.5 vmin;

# }

# .box{

#     height: 18vmin;

#     width: 18vmin;

#     border-radius: 2rem;

#     background-color: #559CAD;

#     box-shadow: 0 0 1rem rgb(0, 0,0.1);

#     border: none;

#     font-size: 8vmin;

#     color: rgb(41, 21, 63) ;

#     cursor: pointer;

# 

# }

# \#reset{

#     padding: 1 rem;

#     font-size:x-large;

#     color: white;

#     background-color: black;

#     border-radius: 1rem;

# }

# \#new\_game{

#     padding: 1 rem;

#     font-size:x-large;

#     color: white;

#     background-color: black;

#     border-radius: 1rem;

#     align-items: end;

# }

# .msg-container{

#     padding: 1 rem;

#     font-size:x-large;

#     color: rgb(7, 160, 71);

#     border-radius: 1rem;

#     background-color: #f5f5f5;

#     align-items: end;

#     align-content: center;

# }

# \#msg{

#  

#     font-size: 5vmin;

# }

# .draw-container{

#     padding: 1 rem;

#     font-size:x-large;

#     color: rgb(240 4 61);

#     border-radius: 1rem;

#     background-color: #F5F5F5;

#     align-items: end;

#     align-content: center;

# }

# \#draw-game{

#      font-size: 5vmin;

# }

# .hide{

#     display: none;

# }

# ***3= JAVA SCRIPT CODE***

# let boxes=document.querySelectorAll(".box");

# let resetbtn=document.querySelector("#reset");

# let newGame=document.querySelector("#new\_game");

# let msg\_con=document.querySelector(".msg-container");

# let msg=document.querySelector("#msg");

# let draw\_con=document.querySelector(".draw-container");

# let draw\_game=document.querySelector("#draw-game")

# 

# 

# let turnO=true;

# 

# let winpatterns=\[

# &nbsp;   \[0,1,2],

# &nbsp;   \[0,4,8],

# &nbsp;   \[0,3,6],

# &nbsp;   \[1,4,7],

# &nbsp;   \[2,5,8],

# &nbsp;   \[2,4,6],

# &nbsp;   \[3,4,5],

# &nbsp;   \[6,7,8]

# ];

# const resetbutton=()=>{

# &nbsp;   let turnO=true;

# &nbsp;   enablesboxes();

# &nbsp;   msg\_con.classList.add("hide");

# 

# }

# boxes.forEach((box) => {

# &nbsp;   box.addEventListener("click", () => {

# &nbsp;   if (turnO){//if turn of O

# &nbsp;       box.innerText="O"

# &nbsp;       box.style.color="white"

# &nbsp;       turnO=false

# &nbsp;   }else{// if tunr of X

# &nbsp;       box.innerText="X"

# &nbsp;       box.style.color="black"

# &nbsp;       turnO=true

# &nbsp;   }

# &nbsp;   box.disabled=true

# &nbsp;   checkwinner();

# &nbsp;   })

# })

# const disabledboxes=()=>{

# &nbsp;   for(let box of boxes){

# &nbsp;       box.disabled=true

# &nbsp;   }

# }

# const enablesboxes=()=>{

# &nbsp;   for(let box of boxes){

# &nbsp;       box.disabled=false

# &nbsp;       box.innerText="";

# &nbsp;   }

# }

# 

# const showWinner=(winner)=>{

# &nbsp;  msg.innerText=`Congratulation Winner is ${winner}`;

# &nbsp;  msg\_con.classList.remove("hide");

# &nbsp;  disabledboxes(); 

# }

# 

# const draw=()=>{

# &nbsp;   draw\_game.innerText=`Oops the match is draw`

# &nbsp;   draw\_con.classList.remove("hide")

# }

# 

# const checkwinner=()=>{

# &nbsp;   hasWin=false;

# &nbsp;   for (let pattern of winpatterns){

# &nbsp;       let pos1val= boxes\[pattern\[0]].innerText;

# &nbsp;       let pos2val= boxes\[pattern\[1]].innerText;

# &nbsp;       let pos3val= boxes\[pattern\[2]].innerText;

# &nbsp;       if (pos1val!="" \&\& pos2val!="" \&\& pos3val!=""){

# &nbsp;           if (pos1val===pos2val \&\& pos2val===pos3val){

# &nbsp;               showWinner(pos1val)

# &nbsp;                hasWin=true;

# &nbsp;           }

# &nbsp;       }

# &nbsp;   }

# &nbsp;   if(!hasWin){

# &nbsp;       allboxes=\[...boxes].every((box)=>box.innerText!="");

# &nbsp;           if(allboxes){

# &nbsp;               draw();

# &nbsp;       }

# &nbsp;   }

# &nbsp;   

# }  

# newGame.addEventListener("click",resetbutton);

# resetbtn.addEventListener("click",resetbutton);

# let n=0

# const scoreboard=()=>{

# &nbsp;   for(n=0;n<6;n++)

# &nbsp;       if(pos1val===turnX)

# &nbsp;           playerX.add

# &nbsp;       else

# &nbsp;           playerO.push(n++)

# }

