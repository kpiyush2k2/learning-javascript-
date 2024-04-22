# Projects ralated to DOM

## project link 
[click](https://stackblitz.com/edit/dom-project-chaiaurcode?file=1-colorChanger%2Fchaiaurcode.js)

# solution code

# project 1

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

# project 2

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
