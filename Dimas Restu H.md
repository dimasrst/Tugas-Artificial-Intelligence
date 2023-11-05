# Dimas Restu H_5311421024
## Artificial Intelligence
## GAME TIC TAC TOE
Dalam penugasan artificial intelligence kali ini, telah dibuat sebuah implementasi permainan Tic-Tac-Toe yang dimodifikasi untuk mendukung papan berukuran variabel (dalam contoh ini, ukuran 4x4) dengan empat pemain yang bersaing. Tujuan dari penugasan ini adalah untuk mengembangkan sebuah permainan yang memungkinkan pemain untuk bermain dengan kecerdasan buatan (AI) sebagai lawan. Kode tersebut memungkinkan pemain untuk bermain pada papan yang lebih besar dengan lebih banyak pemain serta melawan AI yang cerdas dalam memilih langkahnya. Implementasi AI dapat menjadi pengembangan lebih lanjut, di mana AI dapat memilih langkahnya dengan berdasarkan strategi dan kecerdasan buatan yang lebih canggih. Secara keseluruhan, kode ini memberikan dasar yang baik untuk mengimplementasikan permainan Tic-Tac-Toe dengan elemen kecerdasan buatan yang lebih kompleks dalam Python.
Pada awalnya, berencana untuk mengimplementasikan tugas ini menggunakan software NetBeans karena kekuatan Java dalam pengembangan perangkat lunak. Namun, terpaksa beralih ke Python karena perangkat keras yang tersedia tidak memadai untuk menjalankan NetBeans dengan lancar. Python merupakan pilihan yang lebih hemat sumber daya dan memiliki komunitas yang kuat, memungkinkan untuk dengan mudah mengembangkan permainan Tic-Tac-Toe yang mendukung papan berukuran variabel dengan empat pemain tanpa membebani perangkat keras yang terbatas. Keputusan ini juga memungkinkan untuk memfokuskan energi pada aspek permainan dan algoritma, bukan hanya pada pengaturan perangkat pengembangan.
# berikut merupakan hasil codingan dalam python yang sudah dibuat
def print_board(board):
    for row in board:
        print(" | ".join(row))
        print("-" * (6 * len(row) - 1))

def check_winner(board, player):
    n = len(board)
    
    # Check rows, columns, and diagonals
    for i in range(n):
        if all(board[i][j] == player for j in range(n)):
            return True
        if all(board[j][i] == player for j in range(n)):
            return True
    if all(board[i][i] == player for i in range(n)) or all(board[i][n - 1 - i] == player for i in range(n)):
        return True
    
    # Check diagonals from top right to bottom left
    if all(board[i][n - 1 - i] == player for i in range(n)):
        return True
    
    return False

def is_full(board):
    return all(cell != " " for row in board for cell in row)

def main():
    size = 4  # Ukuran papan 4x4
    board = [[" " for _ in range(size)] for _ in range(size)]
    players = ["X", "O", "A", "B"]
    current_player = 0
    winner = None

    while not is_full(board):
        print_board(board)
        row, col = map(int, input(f"Player {players[current_player]}, enter row and column (e.g., 1 2): ").split())
        
        if 1 <= row <= size and 1 <= col <= size:
            if board[row - 1][col - 1] == " ":
                board[row - 1][col - 1] = players[current_player]
                if check_winner(board, players[current_player]):
                    winner = players[current_player]
                    break
                current_player = (current_player + 1) % len(players)
            else:
                print("Cell already filled. Try again.")
        else:
            print("Invalid row or column. Try again.")

    print_board(board)
    if winner:
        print(f"Player {winner} wins!")
    else:
        print("It's a draw!")

if __name__ == "__main__":
    main()

Kode di atas menciptakan permainan Tic-Tac-Toe dengan 4 pemain pada papan 4x4. Setiap pemain diwakili oleh karakter unik ("X", "O", "A", "B"), dan aturan kemenangan berlaku untuk baris, kolom, diagonal, serta diagonal dari kanan atas ke kiri bawah.




