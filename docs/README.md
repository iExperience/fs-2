# iXperience Full Stack 2019 - Day 2

[[toc]]

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