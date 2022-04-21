https://github.com/Sangeetha-Bhuyan/Math4Kids/blob/main/style.css 
const option1 = document.getElementById("option1"),
      option2 = document.getElementById("option2"),
      option3 = document.getElementById("option3"),
  //these three options give acess to the three possible answers
      audio = document.getElementById("myAudio");  
  //this connects the audio 
var answer = 0;
//variable that represent the answer

//create a function to generate an equation
function generate_equation(){ 
  var num1 = Math.floor(Math.random() * 16),
  //this creates the first number using the built in functions math.floor and math.random to generate a random number between 0-15
      num2 = Math.floor(Math.random() * 16),
      wrongAnswer1 = Math.floor(Math.random() * 50),
  //wrongAnswer1 and 2 are the wrong answer numbers generated 
      wrongAnswer2 = Math.floor(Math.random() * 50),
      allAnswers = [],
    //this is an array that stores all of the answers
      switchAnswers = [];
    //this is an array that switch the answers between the indexes of the allAnswers array

  answer = eval(num1 * num2);
  //this creates the correct answer by multiplying number one and number 2
  
  document.getElementById("num1").innerHTML = num1; 
  //this connect the num1s in the HTML to be displayed on the screen
  document.getElementById("num2").innerHTML = num2; 
    //this connect the num2s in the HTML to be displayed on the screen

  allAnswers = [answer, wrongAnswer1, wrongAnswer2];
  //the all answers array is being called and contains the correct answer and the two wrong answers

  for (i = allAnswers.length; i--;){
    //the answers are now shuffled
    switchAnswers.push(allAnswers.splice(Math.floor(Math.random() * (i + 1)), 1)[0]);
    //this switches the answers and the .push inserts them in to the array
  };
  //this shuffles the array so that the three answers are always in a different index (0,1,2)....create a for loop to shuffle

  option1.innerHTML = switchAnswers[0];
  option2.innerHTML = switchAnswers[1];
  option3.innerHTML = switchAnswers[2]; 
  //the answers are now in the switch answers array 

};

option1.addEventListener("click", function(){
  //this activates the option 1 answer with a click on the answer by the user 
    if(option1.innerHTML == answer){
      generate_equation();
      //if option one is the answer than we generate a new equation using the generate_equation function 
    }
    else{
      audio.play();
      //if option one is the wrong answer then the audio file that plays the wrong answer sounds will be activated
    }
});

option2.addEventListener("click", function(){
    if(option2.innerHTML == answer){
      generate_equation();
            //if option two is the answer than we generate a new equation using the generate_equation function 
    }
    else{
      audio.play();
            //if option two is the wrong answer then the audio file that plays the wrong answer sounds will be activated
    }
});

option3.addEventListener("click", function(){
    if(option3.innerHTML == answer){
     generate_equation();
        //if option three is the answer than we generate a new equation using the generate_equation function 
    }
    else{
      audio.play();
            //if option three is the wrong answer then the audio file that plays the wrong answer sounds will be activated
    }
});

generate_equation()
//this is the function call that generates the equation

