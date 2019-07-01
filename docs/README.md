# iXperience Full Stack 2019 - Day 2

[[toc]]

## Document Object Model

### HTML template

DOM HTML template
```html
<!DOCTYPE html>
<html lang="en">

  <head>

    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>FS-Day2</title>
    <link rel="stylesheet" href="style.css">

  </head>

  <body>

    <header>
      <h1>FS Day 2</h1>
    </header>

    <section class="container">
      <form id="my-form">
        <h1>Add User</h1>
        <div class="msg"></div>
        <div>
          <label for="name">Name:</label>
          <input type="text" id="name">
        </div>
        <div>
          <label for="email">Email:</label>
          <input type="text" id="email">
        </div>
        <input class="btn" type="submit" value="Submit">
      </form>

      <ul id="users"></ul>

      <ul class="items">
        <li class="item">Item 1</li>
        <li class="item">Item 2</li>
        <li class="item">Item 3</li>
      </ul>
    </section>

    <script src="main.js"></script>

  </body>

</html>
```

### JS template

DOM JS
main.js
```js
// Single element selectors:
console.log(document.getElementById("my-form"));
console.log(document.querySelector('.item'));

//Multilpe element selector:
console.log(document.querySelectorAll('.item')); //Recomende (Newest)
console.log(document.getElementsByTagName('li'));
console.log(document.getElementsByClassName('item'));

const items = document.querySelectorAll('.item');
console.log(items);
items.forEach(item=>{
  console.log(item);
});

// MANIPULATING THE DOM
const ul = document.querySelector('.items');
// ul.remove();
// ul.lastElementChild.remove();
ul.firstElementChild.textContent = 'Hello';
ul.children[1].innerText = 'Byron';
ul.lastElementChild.innerHTML = '<h1>Hello</h1>';


// EVENTS
const btn = document.querySelector('.btn');
// btn.style.background = 'red';

// Mouse Event
btn.addEventListener('click', e => {
  e.preventDefault();
  console.log(e.target.className);
  document.getElementById('my-form').style.background = '#ccc';
  document.querySelector('body').classList.add('bg-dark');
  ul.lastElementChild.innerHTML = '<h1>Changed</h1>';
});

// Keyboard Event
const nameInput = document.querySelector('#name');
nameInput.addEventListener('input', e => {
  document.querySelector('.container').append(nameInput.value);
});
```

### CSS Tmeplate
styles.css
```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.6;
}

ul {
  list-style: none;
}

ul li {
  padding: 5px;
  background: #f4f4f4;
  margin: 5px 0;
}

header {
  background: #f4f4f4;
  padding: 1rem;
  text-align: center;
}

.container {
  margin: auto;
  width: 500px;
  overflow: auto;
  padding: 3rem 2rem;
}

#my-form {
  padding: 2rem;
  background: #f4f4f4;
}

#my-form label {
  display: block;
}

#my-form input[type='text'] {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

.btn {
  display: block;
  width: 100%;
  padding: 10px 15px;
  border: 0;
  background: #333;
  color: #fff;
  border-radius: 5px;
  margin: 5px 0;
}

.btn:hover {
  background: #444;
}

.bg-dark {
  background: #333;
  color: #fff;
}

.error {
  background: orangered;
  color: #fff;
  padding: 5px;
  margin: 5px;
}
```


## Ionic Navigation

### Home Page TS

```ts{2,12,15-17}
import { Component } from '@angular/core';
import { NavController } from '@ionic/angular';

@Component({
  selector: 'app-home',
  templateUrl: 'home.page.html',
  styleUrls: ['home.page.scss'],
})
export class HomePage {

  constructor(
    private navCtrl: NavController
  ) {}

  navToProfile() {
    this.navCtrl.navigateForward("profile");
  }

}
```

### Home Page HTML

```html{2}
<ion-content>
  <ion-button expand="full" (click)="navToProfile()">Navigate to Profile</ion-button>
</ion-content>
```

### Profile Page HTML

```html{3-5}
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-back-button defaultHref="home"></ion-back-button>
    </ion-buttons>
    <ion-title>profile</ion-title>
  </ion-toolbar>
</ion-header>

<ion-content></ion-content>
```