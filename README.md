# Getting Started With Elm

## Introduction
Lorem ipsum dolor sit amet consectetur adipisicing elit. At quam, delectus quod consequatur asperiores doloremque eaque deleniti assumenda eum, cupiditate fugit laboriosam in, quidem nihil ad explicabo consectetur consequuntur earum!

## Building Our First Elm App: (Hello, Elm!)
### Creating an elm app locally

First we want to install elm on computer. In our terminal:

`npm install -g elm`

To test to see if elm is installed, we write:

`elm -v`

Now let’s cd into the folder and run:

`elm package install elm-lang/html`

You should recieve a prompt, saying:
```bash
Some new packages are needed. Here is the upgrade plan.

  Install:
    elm-lang/core 5.1.1
    elm-lang/html 2.0.0
    elm-lang/virtual-dom 2.0.4

Do you approve of this plan? [Y/n]
```
Hit Y to install the dependencies.
Now elm can compile to html and run in the browser

Writing our elm code from `Main.elm` looks like this:

```elm
module Main exposing (..)

import Html exposing (text)


main = 
    text “Hello, Elm!” 
```

As simple as that! Now let’s compile our code using this command:

`elm make Main.elm — output app.js`

`elm make` is compiling our code into a javascript file called `app.js` and now we can link to an HTML document.

At the root of our project directory we’ll create an index.html to store the script that the compiler generated for us from our Elm file.

```html
<!DOCTYPE html>
<html lang=“en”>
<head>
  <meta charset=“UTF-8”>
  <meta name=“viewport” content=“width=device-width, initial-scale=1.0”>
  <meta http-equiv=“X-UA-Compatible” content=“ie=edge”>
  <title>Hello Elm App</title>
</head>
<body>
  <div id=“app”></div>

  <script src=“app.js”></script>
  <script>
    var appContainer = document.querySelector(‘#app’)
    Elm.Main.embed(appContainer)
  </script>
</body>
</html>
```

We target our div that we created with an id of app in our script tags. We’re telling elm that we will embed our Main.elm file in that div that we assigned to a variable called appContainer.

That’s it. We created our first Elm app. Fire up your browser and open your html file and you should see “Hello, Elm!”.