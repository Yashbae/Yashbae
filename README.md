- 👋 Hi, I’m @Yashbae
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Yashbae/Yashbae is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your class ChessPiece:
    def __init__(self, color, name):
        self.color = color
        self.name = name

    def __str__(self):
        return self.name


class ChessBoard:
    def __init__(self):
        self.board = self.initialize_board()

    def initialize_board(self):
        board = [[" " for _ in range(8)] for _ in range(8)]
        # Place pawns
        for i in range(8):
            board[1][i] = ChessPiece("Black", "P")
            board[6][i] = ChessPiece("White", "P")
        # Place rooks
        board[0][0] = board[0][7] = ChessPiece("Black", "R")
        board[7][0] = board[7][7] = ChessPiece("White", "R")
        # Place knights
        board[0][1] = board[0][6] = ChessPiece("Black", "N")
        board[7][1] = board[7][6] = ChessPiece("White", "N")
        # Place bishops
        board[0][2] = board[0][5] = ChessPiece("Black", "B")
        board[7][2] = board[7][5] = ChessPiece("White", "B")
        # Place queens
        board[0][3] = ChessPiece("Black", "Q")
        board[7][3] = ChessPiece("White", "Q")
        # Place kings
        board[0][4] = ChessPiece("Black", "K")
        board[7][4] = ChessPiece("White", "K")
        return board

    def display(self):
        print("  a b c d e f g h")
        for i, row in enumerate(self.board):
            row_display = f"{8 - i} "
            for square in row:
                row_display += f"{square.name if square != ' ' else '.'} "
            print(row_display)
        print()

    def move_piece(self, start, end):
        start_x, start_y = 8 - int(start[1]), ord(start[0]) - ord("a")
        end_x, end_y = 8 - int(end[1]), ord(end[0]) - ord("a")

        if self.board[start_x][start_y] == " ":
            print("No piece at the starting position!")
            return False

        piece = self.board[start_x][start_y]
        self.board[end_x][end_y] = piece
        self.board[start_x][start_y] = " "
        print(f"Moved {piece.name} from {start} to {end}")
        return True


def main():
    chess_board = ChessBoard()
    chess_board.display()

    while True:
        move = input("Enter your move (e.g., e2 e4) or 'q' to quit: ")
        if move.lower() == "q":
            print("Thanks for playing!")
            break
        try:
            start, end = move.split()
            chess_board.move_piece(start, end)
            chess_board.display()
        except Exception as e:
            print("Invalid input! Please enter a valid move (e.g., e2 e4).")


if __name__ == "__main__":
    main()
