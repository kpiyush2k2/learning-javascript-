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

