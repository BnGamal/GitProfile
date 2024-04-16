# JS
```js


const note = document.querySelector('.note');
const letter = document.querySelector('.letter');
const envelope = document.querySelector('.envelope');
const envelopeBody = document.querySelector('.envelope .body');
const envelopeBodyBottomFlap = document.querySelector('.envelope .body .bottom-flap')
const sealFlapFront = envelope.querySelector('.seal-flap-front');
const sealFlapBack = envelope.querySelector('.seal-flap-back');


let animating = false;
let opened = false;
envelope.addEventListener('click', function() {
    if (!animating) {
        if (!opened) {
            opened = true;
            animating = true;
            sealFlapFront.classList.add('seal-flap-front-animation');
            sealFlapBack.classList.add('seal-flap-back-animation');
            letter.classList.add('letter-animation');
            note.classList.add('remove-note');
            setTimeout(() => {
                animating = false;
            }, 1000);
        } else {
            opened = false;
            sealFlapFront.classList.remove('seal-flap-front-animation');
            sealFlapBack.classList.remove('seal-flap-back-animation');
            letter.classList.remove('letter-animation');
            note.classList.remove('remove-note');
        }
    }
});
```
# html
```html 
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Github Data</title>
	<link rel="stylesheet" href="main.css">
</head>
<body>
  <p class="note">Click on the envelope to open it!</p>

  <div class="envelope">
    <div class="seal-flap-back"></div>
    <div class="letter">hello</div>
    <div class="body">
      <div class="left-shoulder"></div>
      <div class="between-shoulders"></div>
      <div class="right-shoulder"></div>
      <div class="bottom-flap"></div>
    </div>
    <div class="seal-flap-front"></div>
  </div>



	<script src="main.js"></script>
</body>
</html>
```
# css
```css
body {
    background: beige;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    min-height: 600px;
    font-family: sans-serif;
}
.note {
    font-size: 1rem;
    color: #d5d5d5;
    text-align: center;
    max-width: 300px;
    margin: 0 auto;
    transition: 0.5s ease-in-out;
}
/* the content of the letter */
.envelope {
    margin: 2em;
    position: relative;
    width: 51vw;
    height: 30vw;
    max-width: 300px;
    max-height: 176px;
    background: #ff5b1a;
    border-radius: 0 0 15px 15px;
    transition: 1s ease-in-out;
}
.letter {
    position: absolute;
    bottom: 10%;
    width: 80%;
    height: 80%;
    background: white;
    left: 50%;
    transform: translate(-50%, 0);
    border-radius: 15px;
    transition: .5s ease-in-out;
    padding: 1.2em;
    text-align: center;
}
.seal-flap-back {
    position: absolute;
    top: 0;
    width: 100%;
    height: 50%;
    background: rgb(192, 68, 23);
    transform-origin: top;
    transition: 0.5s linear;
    transition-delay: .2s;
    border-radius: 0 0 15px 15px;
    transform: rotateX(90deg);
}
.seal-flap-front {
    position: absolute;
    top: 0;
    width: 100%;
    height: 50%;
    background: #ff9c78;
    transition: 0.5s linear;
    transition-delay: .7s;
    transform-origin: top;
    border-radius: 0 0 15px 15px;
}
.envelope .body {
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: 30% 70%;
}
.left-shoulder {
    background: linear-gradient(to top right, coral 60%, transparent 61%);
}
.right-shoulder {
    background: linear-gradient(to top left, coral 60%, transparent 61%);
}
.body .bottom-flap {
    background: coral;
    grid-column: auto / span 3;
    border-radius: 0 0 15px 15px;
}
/* Animation */
.remove-note {
    opacity: 0;
}
.letter-animation {
    transition-delay: .6s;
    transform: translate(-50%, -40%);
}
.seal-flap-front-animation {
    /* transition: 0.5s ease-in-out; */
    transition-timing-function: ease-in-out;
    transition-delay: 0s;
    transform: rotateX(90deg);
}
.seal-flap-back-animation {
    /* transition: 0.5s ease-in-out; */
    transition-delay: 0.5s;
    transition-timing-function: ease-in-out;
    transform: rotateX(180deg);
 }
```