---
layout: post
title:  "Code Retreat"
date:   2019-11-20 09:00:00 +0200
categories: Exercises
---

tldr;
- A day long, intensive practice event, focusing on the fundamentals of software development and design, away from the pressures of 'getting things done'.
- If you have the change try it out because this workshops are all over the world.

This year was the 10th Anniversary of Code Retreat. It was started by Corey Haines in 2009. The creator also wrote a book "Understanding 4 rules of simple design". The book is short (70 pages) and it is nice introduction on what to expect when attending the Code Retreat.

This year there were more than 150 events around the world. I attended the one organized by Thoughtworks in Munich, Germany.

Code retreat is some kind of workshop. There are about 6 sessions. Each session is 60 minutes long. 45 minutes for the implementation and 15 is the retrospective.

In every session you are implementing the same coding challenge "Conway's Game of Life". The rules for the game are simple. You have grid which contains cells. This cells have two states. They can be dead or alive.
There are 4 rules when the cell changes state in the next generations:
- **Underpopulation**. Living cell is dead if it has less than two neighbor cells that are alive.
- **Survival**. Living cells survives when it has two or three neighbors that are alive.
- **Overcrovding**. Living cell that has more than three neighbor cells that are alive.
- **Reproduction**. Dead cell that has exactly three living neighbor cells becomes alive in the next generation.

<br>
### Constraints

Some constraints that are being used when implementing the Conway's Game of Life coding challenge:
- Program like it’s 1969
- No primitives across method boundaries (input or output)
- Lines of code per method <= 3
- Find the loophole
- Mob programming
- Mute ping-pong pairing

<br>
#### Program like it’s 1969
You can run code only two times. Once on the 30 minute mark and on 45 minute mark.
<br>

<br>
#### No primitives across method boundaries (input or output)
You need to wrap your primitives in your own class.
<br>

<br>
#### Lines of code per method <= 3
The body of the methods needs to be three lines or less.
<br>

<br>
#### Find the loophole
When pair programming you have "good" and "bad" programmer. The good guy tries to write tests that force the other guy to implement the correct solution. Te "bad" programmer tries to implement solution that pass all the tests but not be a general solution. The "good" programmer wins if the final solution works and the "bad" programmer wins if he passes the tests with some trickeries that breaks the code when running it.
<br>

<br>
#### Mob programming
You have 4-6 programmers that try to solve problem together. You have driver and navigator. Driver only listens to navigator for instructions. Navigator can listen to suggestions form the rest of the participants.
<br>

<br>
#### Mute ping-pong pairing
Just like ping-pon pair programming but the participants should not talk to each other. If you don't know what ping-pong pair programming is here is the gist of it. So you do regular pair programming session but with a twist. The first writes a failing test. The other than tries to write implementation and than write failing test and this repeats until the final solution.
<br>
