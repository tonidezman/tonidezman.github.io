---
layout: post
title: 'Building a State Machine'
date: 2020-05-27 09:00:00 +0200
categories: SideProjects
---

I have been doing coding challenges every day and found interesting approach on
how to solve `Valid Number?` coding challenge.

> The challenge is to create function that will take string and return boolean

```javascript
4.325 is a valid number.
1.1.1 is NOT a valid number.
222 is a valid number.
22. is NOT a valid number.
0.1 is a valid number.
22.22. is NOT a valid number.
1. is NOT a valid number.
```

You can try this for yourself and implement the function bellow.

```javascript
function isNumberValid(string) {
  //TODO: Write - Your - Code
}
```

## Hints

- use regex or
- implement state machine

<br>... <br> <br>

## Solution

![state machine for valid number challenge](/assets/state-machine-is-number-valid.png)

To solve this problem with state machine we can have object that contains
`different states` and a `nextState function` that would make transition from
one state to the next.

```javascript
const STATE = {
  START: 'START',
  INTEGER: 'INTEGER',
  DECIMAL: 'DECIMAL',
  AFTER_DECIMAL: 'AFTER_DECIMAL',
  UNKNOWN: 'UNKNOWN',
};

function nextState(state, chr) {
  const isInteger = chr >= '0' && chr <= '9';
  if (state === STATE.START) {
    if (isInteger) return STATE.INTEGER;
    return STATE.UNKNOWN;
  }

  if (state === STATE.INTEGER) {
    if (isInteger) return STATE.INTEGER;
    if (chr === '.') return STATE.DECIMAL;
  }

  if (state === STATE.DECIMAL) {
    if (isInteger) return STATE.AFTER_DECIMAL;
    return STATE.UNKNOWN;
  }

  if (state === STATE.AFTER_DECIMAL) {
    if (isInteger) return STATE.AFTER_DECIMAL;
    return STATE.UNKNOWN;
  }
}

function isNumberValid(string) {
  let currState = STATE.START;
  for (let chr of string) {
    currState = nextState(currState, chr);
    if (currState == STATE.UNKNOWN) return false;
  }
  if (currState === STATE.DECIMAL) return false;
  return true;
}
```
