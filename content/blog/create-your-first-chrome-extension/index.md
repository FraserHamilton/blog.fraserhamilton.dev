---
title: Create your first chrome extension
date: '2020-07-08T12:22:00.000Z'
description: 'Build a simple Pomodoro timer extension in 25 minutes'
---

Chrome is a great browser and part of what makes it so great is how extensible it is. There's a whole library of extensions to choose from to shape it to your specific use case. It's possible that the extension that you're looking for doesn't exist yet, in which case you're going to have to build it. Although it sounds daunting it's actually fairly simple.

In this article I'm going to talk you through building a simple Pomodoro timer extension. The Pomodoro technique is a time management technique where work is broken down into intervals of 25 minutes, separated by short breaks.

## Getting set up

First thing we're going to do is a create a new directory, I've called mine 'pomdoro-extension' but you can name it whatever you want. This directory will contain all the files we need for our extension and most importantly our `manifest.json`.

The extension manifest is the heart of any extension, it's where you'll define stuff like a name for extension as well as configure permissions and files. We'll just add a bare bones `manifest.json` for now.

```json
{
  "name": "Pomodoro Timer",
  "version": "1.0",
  "description": "Simple Pomodoro Timer Extension",
  "manifest_version": 2
}
```

<br/>

Next we need to load our extension into the browser, open up `chrome://extensions` and hit the toggle in the top right to enable developer mode. Then hit 'load unpacked' and select the directory you created earlier. Your extension should now appear in the list of extensions, it won't be able to do anything yet but when we make changes we can just come back to this page and hit the reload button to update the extension.

## Start coding

We want our timer to be accessible through a pop up when we click on our extension icon to the right of the address bar. To do so we need to define a 'browser action'. We'll need to create two new files, a `popup.html` and `popup.js`. Here's the contents of my `popup.html`:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Pomodoro Timer</title>
    <script src="popup.js"></script>
  </head>
  <body>
    <h1>Pomodoro</h1>
    <h2 id="time">25:00</h2>
    <button id="start">Start</button>
    <button id="reset">Reset</button>
  </body>
</html>
```

<br/>

And my `popup.js` file:

```javascript
let myInterval = null

const startTimer = (duration, display) => {
  var timer = duration,
    minutes,
    seconds
  myInterval = setInterval(() => {
    minutes = parseInt(timer / 60, 10)
    seconds = parseInt(timer % 60, 10)

    minutes = minutes < 10 ? '0' + minutes : minutes
    seconds = seconds < 10 ? '0' + seconds : seconds

    display.textContent = minutes + ':' + seconds

    if (--timer < 0) {
      timer = duration
    }
  }, 1000)
}

const resetTimer = display => {
  if (myInterval) {
    clearInterval(myInterval)
  }
  display.textContent = '25:00'
}

window.onload = function() {
  const duration = 60 * 25,
    display = document.querySelector('#time'),
    start = document.querySelector('#start'),
    reset = document.querySelector('#reset')

  start.addEventListener('click', () => startTimer(duration, display))

  reset.addEventListener('click', () => resetTimer(display))
}
;``
```

<br/>

Next we need to add these files to our `manifest.json` as a browser action like so:

```json
{
  "name": "Pomodoro Timer",
  "version": "1.0",
  "description": "Simple Pomodoro Timer Extension",
  "manifest_version": 2,
  "browser_action": {
    "default_popup": "popup.html"
  }
}
```

<br/>

Now if you reload your extension you should be able to trigger the browser action by clicking on your extensions icon. It should look like this:

![alt text](./pomodoro.PNG 'Extension Screenshot')

Hitting start should begin the countdown and reset should put it back to the start and there you have it your first chrome extension, not as difficult as you thought was it?

## Publishing

Okay so no our simple pomodoro timer app is complete how would we go about publishing it? Finish up your testing and then zip your repository. Next create an account over at the [Chrome Webstore Developer Dashboard](https://chrome.google.com/webstore/developer/dashboard).

Hit the "Add new item" button and upload your `.zip` file. You'll need to pay a \$5 developer fee to upload your extension and then once you add a description and pictures you should be all set to publish to the store.
