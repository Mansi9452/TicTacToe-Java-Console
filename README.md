# TicTacToe-Java-Console
# Tic Tac Toe Console Game

This is a simple Tic Tac Toe game implemented in Java for the console.

## How to Play

1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/your-repository-name.git
Here is the corrected and logically improved version of your Tic Tac Toe game in Java:

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Random;
import java.util.Scanner;

public class TicTacToe {
    static ArrayList<Integer> playerPositions = new ArrayList<>();
    static ArrayList<Integer> cpuPositions = new ArrayList<>();

    public static void main(String[] args) {
        char[][] gameBoard = {
            {' ', '|', ' ', '|', ' '},
            {'-', '+', '-', '+', '-'},
            {' ', '|', ' ', '|', ' '},
            {'-', '+', '-', '+', '-'},
            {' ', '|', ' ', '|', ' '}
        };

        printGameBoard(gameBoard);
        Scanner scan = new Scanner(System.in);

        while (true) {
            System.out.println("Enter your placement (1-9):");
            int playerPos = scan.nextInt();
            while (playerPositions.contains(playerPos) || cpuPositions.contains(playerPos)) {
                System.out.println("Position taken! Enter a correct position:");
                playerPos = scan.nextInt();
            }

            placePiece(gameBoard, playerPos, "player");

            String result = checkWinner();
            if (result.length() > 0) {
                printGameBoard(gameBoard);
                System.out.println(result);
                break;
            }

            Random rand = new Random();
            int cpuPos = rand.nextInt(9) + 1;
            while (playerPositions.contains(cpuPos) || cpuPositions.contains(cpuPos)) {
                cpuPos = rand.nextInt(9) + 1;
            }

            placePiece(gameBoard, cpuPos, "cpu");

            printGameBoard(gameBoard);

            result = checkWinner();
            if (result.length() > 0) {
                System.out.println(result);
                break;
            }
        }
        scan.close();
    }

    public static void printGameBoard(char[][] gameBoard) {
        for (char[] row : gameBoard) {
            for (char c : row) {
                System.out.print(c);
            }
            System.out.println();
        }
    }

    public static void placePiece(char[][] gameBoard, int pos, String user) {
        char symbol = ' ';
        if (user.equals("player")) {
            symbol = 'X';
            playerPositions.add(pos);
        } else if (user.equals("cpu")) {
            symbol = 'O';
            cpuPositions.add(pos);
        }

        switch (pos) {
            case 1:
                gameBoard[0][0] = symbol;
                break;
            case 2:
                gameBoard[0][2] = symbol;
                break;
            case 3:
                gameBoard[0][4] = symbol;
                break;
            case 4:
                gameBoard[2][0] = symbol;
                break;
            case 5:
                gameBoard[2][2] = symbol;
                break;
            case 6:
                gameBoard[2][4] = symbol;
                break;
            case 7:
                gameBoard[4][0] = symbol;
                break;
            case 8:
                gameBoard[4][2] = symbol;
                break;
            case 9:
                gameBoard[4][4] = symbol;
                break;
            default:
                System.out.println("Invalid position");
                break;
        }
    }

    public static String checkWinner() {
        List<List<Integer>> winningConditions = new ArrayList<>();
        winningConditions.add(Arrays.asList(1, 2, 3));
        winningConditions.add(Arrays.asList(4, 5, 6));
        winningConditions.add(Arrays.asList(7, 8, 9));
        winningConditions.add(Arrays.asList(1, 4, 7));
        winningConditions.add(Arrays.asList(2, 5, 8));
        winningConditions.add(Arrays.asList(3, 6, 9));
        winningConditions.add(Arrays.asList(1, 5, 9));
        winningConditions.add(Arrays.asList(3, 5, 7));

        for (List<Integer> condition : winningConditions) {
            if (playerPositions.containsAll(condition)) {
                return "Congratulations! You won!";
            } else if (cpuPositions.containsAll(condition)) {
                return "CPU wins! Sorry :(";
            } else if (playerPositions.size() + cpuPositions.size() == 9) {
                return "It's a tie!";
            }
        }
        return "";
    }
}
```

### Running the Code in VS Code

1. **Open the Project Folder**:
   - Open VS Code.
   - Go to `File` > `Open Folder...` and select the folder containing your `TicTacToe.java` file.

2. **Set Up Java Environment**:
   - Ensure you have the Java Extension Pack installed in VS Code. If not, install it from the Extensions view (`Ctrl+Shift+X`).

3. **Compile and Run the Code**:
   - Open the terminal in VS Code (`Ctrl+``).
   - Compile the Java file by running:
     ```sh
     javac TicTacToe.java
     ```
   - Run the compiled Java file by executing:
     ```sh
     java TicTacToe
     ```

### Sharing the Project on GitHub

1. **Initialize a Git Repository**:
   - Open the terminal in VS Code.
   - Run the following commands:
     ```sh
     git init
     git add .
     git commit -m "Initial commit"
     ```

2. **Create a Repository on GitHub**:
   - Go to GitHub and create a new repository.
   - Follow the instructions to push your local repository to GitHub:
     ```sh
     git remote add origin https://github.com/yourusername/your-repository-name.git
     git branch -M main
     git push -u origin main
     ```

### README.md Content

Create a `README.md` file in your project folder with the following content:

```markdown
# Tic Tac Toe Console Game

This is a simple Tic Tac Toe game implemented in Java for the console.

## How to Play

1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/your-repository-name.git
   ```
2. Open the project in your favorite IDE or text editor.
3. Compile and run the `TicTacToe.java` file.
   ```sh
   javac TicTacToe.java
   java TicTacToe
   ```
4. Follow the on-screen instructions to play the game.

## Game Rules

- The game is played on a 3x3 grid.
- Players take turns to place their marks (X or O) in an empty cell.
- The first player to get three of their marks in a row (horizontally, vertically, or diagonally) wins.
- If all 9 cells are filled and no player has three in a row, the game is a draw.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

By following these steps, you should be able to set up and run your Java-based Tic Tac Toe game in VS Code and share it on GitHub. If you have any more specific questions or need further assistance, feel free to ask!
