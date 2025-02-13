<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hidden message</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <input type="checkbox" id="heartInput">
    <label for="heartInput" class="hearts" id="heartholder"></label>
    <span class="hearts" id="heart"></span>
    <span class="circle"></span>

    <input type="radio" checked="checked" id="checkENG" name="language">
    <label class="lang" for="checkENG">Eng</label>   

    <div class="message eng">
        <p>You're still my favorite person. Always will be.</p>
        <p class="love">I love you ❤</p>
    </div>
    
    <script src="script.js"></script>
</body>
</html>var heart= document.getElementById('heart'),
    heartW = heart.offsetWidth,
    heartH = heart.offsetHeight;

document.body.onmousemove = function( event ) {
  var x = event.clientX - (heartW / 2);
  var y = event.clientY  - (heartH / 2);
  
  heart.style.transform = "translate("+ x +"px, "+ y +"px) rotate(-45deg)"
}/*Basics*/
* {
  margin: 0;
}

html, body {
  height: 100%;
  margin: 0;
  padding: 0;
  cursor: none;
}

body {
  overflow: hidden;
  
}

input {
  display: none;
}

/*Circle and hearts*/
.circle {
  background: #EF476F;
  border-radius: 50%;
  left: calc(50% - 10px);
  top: 252px;
  transition: all .5s cubic-bezier(0.22, 0.53, 0.37, 1.41);
}

.hearts, .hearts:before, .hearts:after, .circle {
  display: block;
  width: 20px;
  height: 20px;
  position: absolute;
}

.hearts {
  transform: rotate(-45deg);
}

.hearts:before, .hearts:after {
  content: '';
  position: absolute;
  border-radius: 50%;
  background: inherit;
}

.hearts:before {
  left: 12px;
}

.hearts:after {
  top: -12px;
}

#heart {
  background: #D33F49;
  z-index: 2;
  pointer-events: none;
}

#heartholder {
  top: 255px;
  left: calc(50% - 10px);
  cursor: none;
  z-index: 1;
  background: #f697e1;
  transition: all .2s ease-in;
}

/*Transform heart into key*/
#heartholder:hover {
  background: #ad6a9e;
}

#heartholder:hover ~ #heart{
  width: 7px;
  height: 27px;
  background: #ffcf0d;
}


#heartholder:hover ~ #heart:after {
  left: -7px;
  top: -19px;
  width: 12px;
  height: 12px;
  background: transparent;
  border: 5px #ffcf0d solid;
}

#heartholder:hover ~ #heart:before {
  border-radius: 0;
  top: 12px;
  left: 0;
  border-color: #ffcf0d;
  border-width: 4px;
  border-top-style: solid;
  border-bottom-style: solid;
  background: transparent;
  height: 9px;
}

/*Make the circle appear*/
#heartInput:checked ~ .circle {
  width: 400px;
  height: 400px;
  left: calc(50% - 200px);
  top: 50px;
}

/*Message to the loved one*/
.message, label.lang {
  font-family: 'Cabin', sans-serif;
}

.message {
  position: absolute;
  width: 300px;
  color: white;
  font-size: 18px;
  text-align: center;
  margin: 0 auto;
  line-height: 1.5;
  top: 150px;
  left: calc(50% - 150px);
  opacity: 0;
}

.message p:first-child {
  margin-bottom: 70px;
}

.love {
  font-family: 'Lobster', cursive;
  font-size: 30px;
}

/*Change language*/

label.lang {
  margin-right: 15px;
  display: block;
  float: right;
  color: #aaa;
  padding: 15px 5px;
  position: relative;
  z-index: 5;
  cursor: pointer;
}

input[type="radio"]:checked + label, label.lang:hover { 
  font-weight: bold; 
  text-decoration: underline;
  color: #383838;
} 

#checkENG:checked ~ .message.eng {
  opacity: 1;
}

#checkFR:checked ~ .message.fr {
  opacity: 1;
}
