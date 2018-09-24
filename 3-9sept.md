# Week Starting 3rd September

- [Tell, Don't Ask](#tell-dont-ask)
- [Nested Classes](#nested-classes)
- [Enums](#enums)

## Tell, Don't Ask
The _Tell, Don't Ask_ principle suggests that you should tell an object to do something rather than querying the object, doing logic on the result and then telling the object what to do based on the answer - in which case, the logic is probably the responsibility of the object in the first place. This helps ensure that data and logic are kept together and reduces the risk of violating encapsulation.

#### Not a Great Idea
```java
if (gameBoard.isValidMove(userMove)){
    gameBoard.addMove(userMove, currentPlayerToken);
    prompt.printConfirmedMove();
    prompt.printBoard(gameBoard.returnBoard());
    if(gameBoard.isWon()){
        prompt.printWin(currentPlayerToken);
    } else if (gameBoard.isDraw()){
        prompt.printDraw();
    }
}
```
#### Better Idea
```java
Result result = gameBoard.addMoveToBoard(currentMove, currentPlayer);
prompt.print(result);
}
```
#### Further Reading:
- [The Pragmatic Programmer](https://pragprog.com/articles/tell-dont-ask)
- [Martin Fowler](https://martinfowler.com/bliki/TellDontAsk.html)
- [DevIQ](https://deviq.com/tell-dont-ask/)

## Nested Classes
A _nested class_ or _inner class_ is a class that has been defined inside another class.
- Nesting helper classes makes their package more streamlined
- Increases encapsulation
- Leads to more maintainable and readable code
```java
// abstract parent class
public abstract class Result {

    private final GameBoard board;
    private final Status status;

    public Result(GameBoard gb, Status s){
        this.board = gb;
        this.status = s;
    }

    Status getStatus(){
        return this.status;
    }

    GameBoard getBoard(){
        return this.board;
    }

    // nested/inner class
    public static class Draw extends Result {
        public Draw(GameBoard gb) {
            super(gb, Status.DRAW);
        }
    }

    public static class Win extends Result {
        public Win(GameBoard gb) {
            super(gb, Status.WIN);
        }
    }
}
```
#### Further Reading:
- [Java Docs](https://docs.oracle.com/javase/tutorial/java/javaOO/nested.html)

## Enums
Enums are an iterable set of pre-defined constants. Accessed using `Object.ENUM`. 

```java
enum Status {
        WIN ("Congratulations, you've won the game!"),
        DRAW ("Oh no, it's a draw!"),
        ERROR ("Something went wrong, please input another move:"),
        CONTINUE ("Move confirmed, here is the current board:");

        Status (String message){
            this.message = message;
        }
        
        public String getMessage(){
            return this.message;
        }

        private String message;
    }
```
#### Further Reading:
- [Java Docs](https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html)
- [GeeksForGeeks](https://www.geeksforgeeks.org/enum-in-java/)
- [Baeldung](https://www.baeldung.com/a-guide-to-java-enums)