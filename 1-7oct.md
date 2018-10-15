# Week Starting 1st October

- [To-Do This Week](#to-do-this-week)
- [Four Rules of Simple Design](#four-rules-of-simple-design)
- [Ports and Adaptors](#ports-and-adaptors)
- [Tic Tic Toe](#tic-tac-toe)
- [Braindump](#braindump)

## To-Do This Week
- Read up on Four Rules of Simple Design again
- Keep working on Tic Tac Toe

## Four Rules of Simple Design
_A good way to detect knowledge duplication is to ask what happens if we want to change something._

#### Further Reading
- Understanding the Four Rules of Simple Design, Corey Haines

## Ports and Adaptors
_Adaptors_ implement the code that allows the business logic to communicate with specific tools and vice versa.

Adaptors are created to fit specific _ports_, specifications on how the adaptor can use the application core. These ports are usually interfaces. Ports belong inside the application core, while adaptors belong outside.

#### Further Reading
- [Functional Core, Imperative Shell](https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell)

## Braindump
- Four Rules of Simple Design
- Build pipeline
- Clean code

What needs to change?
- Prompt interface
- Console prompt
- how do I make the code wait for the http request?


#### Changes Made
- moved a print from inside gameloop to startgame
- moved 'get player' method to Game instead of Main
- moved 'get player' method to prompt instead of game
- added console adaptor, moved most prompt things to adaptor, made ioadaptor interface
- moved getValidMove to console adaptor