# Projects Related to DOM

## Project Link

[click here] (https://stackblitz.com/edit/dom-project-chaiaurcode?file=index.html)

# Solution Code 

## Project 1 : Color-Changer

```javascript

const body = document.querySelector("body")
const buttons = document.querySelectorAll('.button ')

buttons.forEach(function(button) {
    console.log(button)

    button.addEventListener('click', function(e) {
        console.log(e)
        console.log(e.target)
        if(e.target.id == 'black') {
            body.style.backgroundColor = "#212121"
            body.style.color = "#fff"
        }
        else if(e.target.id == 'blue') {
            body.style.backgroundColor = "blue"
            body.style.color = "black"
        }
        else if(e.target.id == 'yellow') {
            body.style.backgroundColor = "yellow"
        }
        else {
            body.style.backgroundColor = "red"
        }
    })
});

```

## Project 2 : BMI-Calculator

```javascript

const form = document.querySelector('form')

form.addEventListener('submit', function(e) {
    e.preventDefault();

    //extracting the value of height in Numbers(because it gives in string)
    const height = parseInt(document.querySelector('#height').value)
    const weight = parseInt(document.querySelector('#weight').value)
    const result = document.querySelector('.result')

    if(height == '' || height < 0 || isNaN(height)) {
        result.innerHTML = `Pleave give a valid Height: ${height}`
        result.style.padding = "15px"
    }
    else if(weight == '' || weight < 0 || isNaN(weight)) {
        result.innerHTML = `Pleave give a valid Weight: ${weight}`
        result.style.padding = "15px"
    }
    else {
        const bmi = (weight / ((height*height) / 10000)).toFixed(2);
        result.innerHTML = `<span>Body Mass Index: ${bmi}</span>`;
        result.style.padding = "15px"
            
        const under = document.querySelector('#p1')
        const normal = document.querySelector('#p2')
        const over = document.querySelector('#p3')
        if(bmi < 18.6) {
            under.style.display = "block"
            under.style.color = "red"
        }
        else if(bmi >= 18.6 && bmi <= 24.9) {
            normal.style.display = "block"
            normal.style.color = "#67e871"
        }
        else {
            over.style.display = "block"
            over.style.color = "red"
        }
    }
})

```

## Project 3 : Digital-Clock

```javascript

const clock = document.querySelector('.clock')

setInterval(function() {
    let date = new Date()
    //console.log(date.toLocaleTimeString)
    clock.innerHTML = date.toLocaleTimeString();

}, 1000);

```

## Project 4 : Guess-Number

```javascript

let randomNumber = parseInt(Math.random()*100+1)

const submitBtn = document.querySelector('#subt')
const userInput = document.querySelector('#guessField') //input comes in string so we need to convert into number so we use parseInt
const guessSlot = document.querySelector('.guesses')
const remainingGuesses = document.querySelector('.remainingGuess')
const lowOrHigh = document.querySelector('.lowOrHigh')
const startOver = document.querySelector('.resultParas')

const p = document.createElement('p')

let prevGuesses = []
let numOfGuess = 1
let playGame = true

if(playGame) {
    submitBtn.addEventListener('click', (e) => {
        e.preventDefault();
        //converting input value into number
        const numIs = parseInt(userInput.value)
        validateGuess(numIs)
    })
}

function validateGuess(guess) {
    if(isNaN(guess)) {
        alert("Please enter a valid number")
    }
    else if(guess < 1) {
        alert("Please enter a number more than 1")
    }
    else if(guess < 1) {
        alert("Please enter a number less than 100")
    }
    else {
        prevGuesses.push(guess)
        if(numOfGuess === 10) {
            displayGuess(guess);
            displayMessage(`Game Over. Random Number was: ${randomNumber}`)
            endGame();
        }
        else {
            displayGuess(guess)
            checkGuess(guess)
        }
    }
}

function checkGuess(guess) {
    if(guess == randomNumber) {
        displayMessage(`You guessed it right`)
        endGame()
    }
    else if(guess < randomNumber){
        displayMessage(`Number is Tooo low`)
    }
    else if(guess > randomNumber){
        displayMessage(`Number is Tooo high`)
    }
}

//Cleanup Function
function displayGuess(guess) {
    userInput.value = ''
    guessSlot.innerHTML += `${guess} `
    numOfGuess++;
    remainingGuesses.innerHTML = `${11-numOfGuess}`
}

function displayMessage(message) {
    lowOrHigh.innerHTML = `<h3>${message}</h3>`
}

function endGame() {
    userInput.value = ''
    userInput.setAttribute('disabled', '')
    playGame = false
    const newGameBtn1 = document.querySelector('#btn2')
    newGameBtn1.style.display = "block"
    newGame()
}



function newGame() {
    const newGameBtn = document.querySelector('#btn2')

    newGameBtn.addEventListener('click', (e) => {
        randomNumber = parseInt(Math.random()*100+1)
        prevGuesses = []
        numOfGuess = 1
        guessSlot.innerHTML = ''
        lowOrHigh.innerHTML = ''
        remainingGuesses.innerHTML = `${11-numOfGuess}`
        userInput.removeAttribute('disabled')
        playGame = true
        newGameBtn.style.display = "none"
    })
}

```

## Project 5 : Color-Changer

```javascript



```