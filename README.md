# Plane-Jane-Modal

This past week I was lucky enough to take part in a tech interview. One of the challenges I was asked to complete was to make a modal using html, css, and javaScript. This caught me off guard because a modal seemed so different than other components. I implemented how I thought the javaScript should look like and the html was all provided, but I was stuck on the type of styling a modal has. So after the interview I went ahead and did a little research and finished the challenge, and I wanted to share how to create a basic modal.

## HTML 
First off lets start with the html. Create a file called index.html and set up the basic doctype of html.
```
#index.html

<!DOCTYPE html>
<html>

<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width">
	<title>repl.it</title>
	<link href="style.css" rel="stylesheet" type="text/css" />
</head>

<body>

	<div class="modal-wrapper">
		<div class="modal-content">
			<div class="modal-close">X</div>

			<h1>Hi, here is my modal content</h1>

			<p>More modal content to look at More modal content to look at</p>

		</div>
	</div>

	<div class="page-content">
		<h1>HTML Page Content</h1>

		<p>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. <em>Aenean ultricies mi vitae est.</em> Mauris placerat eleifend leo. Quisque sit amet est et sapien ullamcorper pharetra. Vestibulum erat wisi, condimentum sed, <code>commodo vitae</code>, ornare sit amet, wisi. Aenean fermentum, elit eget tincidunt condimentum, eros ipsum rutrum orci, sagittis tempus lacus enim ac dui. <a href="#" class="modal-open">Donec non enim</a> in turpis pulvinar facilisis. Ut felis.</p>

      <h2>Header Level 2</h2>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
      </p>
     
    </div>

    <script src="script.js"></script>
  </body>
</html>
```
The only important things for the modal we need to pay attention to here is the `div` with a class of `modal-wrapper`, and the link with a class of `modal-open` which we will use javascript to add an event listener and run some more code. Also be aware of the `script` tag in the bottom which will connect the javaScript file we are about to make to our html file and the `link` tag to our stylesheet.


## The JavaScript
Now create a file named `script.js`. The basic code we need will look like this.
```
#script.js

let modalLink = document.getElementsByClassName('modal-open')[0]
let modalWrapper = document.getElementsByClassName('modal-wrapper')[0]
let modalClose = document.getElementsByClassName('modal-close')[0]

  modalLink.addEventListener("click", function(event) {
  if (modalWrapper.className === 'modal-wrapper') {
    modalWrapper.classList.add('active')
    event.preventDefault()
  }
} )

modalClose.addEventListener('click', function (event) {
  modalWrapper.classList.remove('active')
  event.preventDefault()
})
```
We declare three variables with the values of all the elements we will need to have access to, and we have two event listeners. The first eventListner is attached to our link, and will add a class of `active` to `modalWrapper` which will add the `active` styling properties in style.css once made. The second eventListener is for when our modal is open and is attached to the modalClose element which is an `x`.


## Css
Create a file named `style.css`.
```
#style.css

body {
  position: relative;
  margin: 0;
}

.active {
    z-index: 3;
    padding-top: 100px;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgba(0,0,0,0.4);
    display: flex;
    padding: 0;
}

.modal-content {
   background-color: #fff;
    outline: 0;
    padding: .1rem 15px;
    margin: auto;
    width: 90%;
    max-width: 500px;
}

.modal-wrapper:not(.active) {
  display: none;
}

.modal-close {
  cursor: pointer;
}

```
You can see when we style the class `active` we add a `z-index` of 3 which will put it ahead of the other elements in the stack order. We also give it a position of `absolute` which will keep it positioned relative to it's parent element. Then we add some styling to `.modal-content` to give it the desired look.

There are other ways to accomplish this effect, but this way was relative to the requirements of the coding challenge. I learned something new and it was not as difficult as I had thought it was!
