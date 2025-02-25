# Projects Related to DOM/Events

# Solution Code 

## Project 1 : Unlimited-Colors

```javascript

//Random colors generate

//hex values = total 16(0-9 and ABCDEF)
const randomColor = function() {
    const hex = '0123456789ABCDEF';
    let color = '#';
    for(let i=0; i<6; i++) {
        const randomNumber = Math.floor(Math.random() * 16); // generate random number 0 to 16
        color += hex[randomNumber];
    }
    return color;
}
// console.log(randomColor())

let intervalId;
const startChangingColor = function(){
    if(!intervalId) {
        intervalId = setInterval(changeBgColor, 500); //500 == 0.5 sec
    }

    function changeBgColor() {
        document.body.style.backgroundColor = randomColor();
    }
};

const stopChangingColor = function(){
    clearInterval(intervalId);
    intervalId = null;
};

const startBtn = document.querySelector("#startBtn");
const stopBtn = document.querySelector("#stopBtn");
startBtn.addEventListener('click', startChangingColor)
stopBtn.addEventListener('click', stopChangingColor)

```

## Project 2 : Keyboard-magic

```javascript

    const insert = document.getElementById('insert');
    window.addEventListener('keydown', (e) => {
        insert.innerHTML = `
            <div class="color">
                <table>
                    <tr>
                        <th>Key</th>
                        <th>Keycode</th>
                        <th>Code</th>
                    </tr>
                    <tr>
                        <td>${e.key == ' ' ? 'space' : e.key}</td>
                        <td>${e.keyCode}</td>
                        <td>${e.code}</td>
                    </tr>
                </table>
            </div>
        `;
    });

```