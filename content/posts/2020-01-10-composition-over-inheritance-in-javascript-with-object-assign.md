---
template: post
title: Composition Over Inheritance in Javascript with Object.assign()
slug: composition-over-inheritance-in-javascript
draft: true
date: 2020-01-10T14:15:16.893Z
description: todo
category: javascript
tags:
  - OOP
  - javascript
  - composition
---
Lets say you have a Werewolf class

```javascript
class Werewolf {
  constructor(name) {
    this.name = name
  }
  
  bite() {
    console.log(`*${this.name} just bit you*`);
  }
  
  howl() {
    console.log(`Ahwoooooooooo! I'm ${this.name}`);
  }
}
```

Our Werewolf is now able to bite and to howl, a pretty basic summary of what werewolves do, but let's leave it like that for now.

In our Forbidden Forest we want to have some spiders, so let's make that class too

```javascript
class Spider {
  constructor(name) {
    this.name = name;
  }
  
  bite() {
    console.log(`*${this.name} just bit you*`)
  }
  
  crawl() {
    console.log(`TickyClickTick... I'm ${this.name}`)
  }
}
```

Both werewolves and spiders bite, so we create a Parent class with this feature following the DRY (Don't Repeat Yourself) principle.

```javascript
class Creature {
  constructor(name) {
    this.name = name;
  }
  
  bite() {
    console.log(`*${this.name} just bit you*`);
  }
}

class Werewolf extends Creature {
  howl() {
    console.log(`Ahwoooooooooo! I'm ${this.name}`);
  }
}

class Spider extends Creature { 
  crawl() {
    console.log(`TickyClickTick... I'm ${this.name}`);
  }
}
```
