# Hannaam-ba
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Amőba Játék</title>
    <style>
        .cell {
            width: 50px;
            height: 50px;
            border: 1px solid black;
            display: inline-block;
            font-size: 30px;
            text-align: center;
            line-height: 50px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Amőba Játék</h1>
    <div id="board">
        <!-- Itt fog megjelenni a játéktábla -->
    </div>

    <script>
        // Létrehozzuk a játéktáblát egy mátrixként
        const boardSize = 3; // 3x3-as játéktábla
        let board = [];
        for (let i = 0; i < boardSize; i++) {
            board.push(new Array(boardSize).fill(''));
        }

        // Ellenőrizzük, melyik játékos következik
        let currentPlayer = 'X';

        // Játéktábla HTML megjelenítése
        const boardContainer = document.getElementById('board');
        for (let i = 0; i < boardSize; i++) {
            for (let j = 0; j < boardSize; j++) {
                const cell = document.createElement('div');
                cell.classList.add('cell');
                cell.dataset.row = i;
                cell.dataset.col = j;
                cell.addEventListener('click', handleCellClick);
                boardContainer.appendChild(cell);
            }
            boardContainer.appendChild(document.createElement('br'));
        }

        // Cellákra kattintás kezelése
        function handleCellClick(event) {
            const row = event.target.dataset.row;
            const col = event.target.dataset.col;
            if (board[row][col] === '') { // Ellenőrizzük, hogy a cella üres-e
                board[row][col] = currentPlayer;
                event.target.innerText = currentPlayer;
                // Játékos váltása
                currentPlayer = (currentPlayer === 'X') ? 'O' : 'X';
            }
        }
    </script>
</body>
</html>
