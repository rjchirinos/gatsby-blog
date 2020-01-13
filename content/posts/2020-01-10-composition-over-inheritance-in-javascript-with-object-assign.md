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
    `${this.name} just bit you`
  }
  
  howl() {
    console.log(`Ahwoooooooooo! I'm ${this.name}`);
  }
}
```
