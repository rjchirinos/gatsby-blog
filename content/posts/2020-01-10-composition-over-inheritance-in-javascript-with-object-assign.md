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
    this.name = name;
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
    console.log(`*${this.name} just bit you*`);
  }
  
  crawl() {
    console.log(`TickyClickTick... I'm ${this.name}`);
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

Cool, now we have a fancy forest with spiders and werewolves, but we need some adults to protect all of the students from these creatures, so let's make a Professor class.

```javascript
class Professor {
  constructor(name) {
    this.name = name;
  }
  
  teach() {
    console.log(`I'm professor ${this.name}, open your books`);
  }
  
  spell() {
    console.log(`${this.name}: "Stupefy"`);
  }
}
```

But professors are not the only ones who can cast spells, and lately there have been horrible news about Death Eaters killing people, as if werewolves and spiders were not enough in this magical world.

```javascript
class DeathEater {
  constructor(name) {
    this.name = name;
  }
  
  kill() {
    console.log(`${this.name}: "Avada Kedavra"`);
  }
  
  spell() {
    console.log(`${this.name}: "Stupefy"`);
  }
}
```

So we create a parent class for this pair too.

```javascript
class Wizard {
  constructor(name) {
    this.name = name;
  }
  
  spell() {
    console.log(`${this.name}: "Stupefy"`);
  }
}

class Professor extends Wizard {  
  teach() {
    console.log(`I'm professor ${this.name}, open your books`);
  }
}

class DeathEater extends Wizard {
  kill() {
    console.log(`${this.name}: "Avada Kedavra"`);
  }
}
```

For now our magic school scheme looks like this

```
Creature {
  .bite()
  
  Werewolf {
    .howl()
  }
  
  Spider {
    .crawl()
  }
}

Wizard {
  .spell()
  
  Professor {
    .teach()
  }
  
  DeathEater {
    .kill()
  }
}
```

We can be happy now, we have a pretty magical word with werevolves, wizards and spiders, a pair of books come and go and everybody seems to like the schema we design. Inheritance help us to solve some repetitive code and makes our product more organized, what could be wrong?
