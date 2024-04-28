# Projects ralated to DOM

## project link 
[click](https://stackblitz.com/edit/dom-project-chaiaurcode?file=1-colorChanger%2Fchaiaurcode.js)

# solution code

## project 1

``` javascript
const buttons = document.querySelectorAll(".button")
const body = document.querySelector("body")

buttons.forEach( function(button)  {
  console.log(button);
  // event mouse click only used here
  button.addEventListener('click',function(event){
    console.log(event);
    console.log(event.target);
    if(event.target.id === 'grey'){
      body.style.backgroundColor = event.target.id
    }
    if(event.target.id === 'white'){
      body.style.backgroundColor = event.target.id
    }
    if(event.target.id === 'blue'){
      body.style.backgroundColor = event.target.id
    }
    if(event.target.id === 'yellow'){
      body.style.backgroundColor = event.target.id
    }
    
  });
});


```

## project 2

``` javascript
const form = document.querySelector('form')
/* cause we are using form here event will be submit type*/

// if we take inputs of heights and weights here this usecase will give us empty value

/* whenever a form is submitted it is
submitted by post or get type. but when submitted it gets stored in server. we have
to stop that as we aren't storing it on server*/
form.addEventListener('submit', function(event){
  event.preventDefault()  // to stop storing in server
  const height = parseInt(document.querySelector('#height').value)
  const weight = parseInt(document.querySelector('#weight').value)
  const results = document.querySelector('#results')

  if(height === '' || height < 0 || isNaN(height)){
    results.innerHTML = `please give a valid height ${height}`;
  }
  else if(weight === '' || weight < 0 || isNaN(weight)){
    results.innerHTML = `please give a valid weight ${weight}`;
  }
  else {
    // bmi formula
    const bmi = (weight / ((height*height)/10000)).toFixed(2);  // toFixed(2) used to prevent large values after decimal, it will take on 2 values after decimal

    let bmiCategory;
    if (bmi < 18.5) {
      bmiCategory = "Underweight";
    } else if (bmi >= 18.5 && bmi < 25) {
      bmiCategory = "Normal weight";
    } else {
      bmiCategory = "Overweight";
    }

    results.innerHTML = `<span>${bmi}</span><br><span>${bmiCategory}</span>`;
    
  }
  
});
```

## project 3

``` javascript
const clock = document.getElementById('clock')
//const clock1 = document.querySelector('#clock')

let date = new Date()
console.log(date.toLocaleTimeString());


setInterval(function(){
  let date = new Date()
  // console.log(date.toLocaleTimeString());
  clock.innerHTML = date.toLocaleTimeString();
}, 1000);

```

## project 4

``` javascript
let randomNumber = parseInt(Math.random() * 100 + 1);
const submit = document.querySelector('#subt');
const userInput = document.querySelector('#guessField');
const guessSlot = document.querySelector('.guesses');
const remaining = document.querySelector('.lastResult');
const lowOrHi = document.querySelector('.lowOrHi');
const startOver = document.querySelector('.resultParas');

const p = document.createElement('p');


let prevGuess = []
let numGuess = 1

let playGame = true
if(playGame){
  submit.addEventListener('click', function(event){
    event.preventDefault()
    const guess = parseInt(userInput.value)
    console.log(guess);
    validateGuess(guess)
  });
}
function validateGuess(guess){
  // method checks whether our guess is btw 1 to 100
  if(isNaN(guess)){
    alert('please enter a valid number')
  }else if(guess < 1){
    alert('please enter a number > 1')
  }else if(guess > 100){
    alert('please enter a number < 100')
  }else {
    prevGuess.push(guess)
    if(numGuess === 11){
      displayGuess(guess)
      displayMessage(`Game Over. Random number was ${randomNumber}`)
      endGame()
    }else{
      displayGuess(guess)
      checkGuess(guess)
    }
  }

}

function checkGuess(guess){
  // print msg that our guess is correct or not, low or high
  if(guess === randomNumber){
    displayMessage(`You guessed it right`)
    endGame()
  }else if(guess < randomNumber){
    displayMessage(`number is Too low`)
  }else if(guess > randomNumber){
    displayMessage(`number is Too high`)
  }
}

function displayGuess(guess){
  userInput.value = '';
  guessSlot.innerHTML += `${guess}, `;
  numGuess++;
  remaining.innerHTML = `${11 - numGuess}`;
}
function displayMessage(message){
  // this function directly interacts with DOM
  lowOrHi.innerHTML = `<h2>${message}</h2>`
}

function endGame(){
  userInput.value = '';
  userInput.setAttribute('disabled', '')
  p.classList.add('button')
  p.innerHTML = `<h2 id="newGame">Start new Game</h2>`;
  startOver.appendChild(p);
  playGame = false;
  newGame();
}

function newGame(){
  const newGameButton = document.querySelector('#newGame')
  newGameButton.addEventListener('click', function(event){
    randomNumber = parseInt(Math.random() * 100 + 1);
    prevGuess = [];
    numGuess = 1;
    guessSlot.innerHTML = ''
    remaining.innerHTML = `${11 - numGuess}`;
    userInput.removeAttribute('disabled')
    startOver.removeChild(p);
    
    playGame = true;
  });
}
```