<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Jogo da Velha</title>
  <style>
    /* estilo das células do tabuleiro */
    .cell {
      width: 100px;
      height: 100px;
      border: 1px solid black;
      text-align: center;
      vertical-align: middle;
      font-size: 72px;
      font-weight: bold;
      cursor: pointer;
    }
    
    /* estilo para destacar a célula selecionada */
    .cell.selected {
      background-color: #d9d9d9;
    }
    
    /* estilo para destacar a célula vencedora */
    .cell.winner {
      background-color: #ffd9b3;
    }
    
    /* estilo para o texto de vitória */
    .winner-text {
      font-size: 24px;
      font-weight: bold;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>Jogo da Velha</h1>
  <table>
    <tr>
      <td class="cell"></td>
      <td class="cell"></td>
      <td class="cell"></td>
    </tr>
    <tr>
      <td class="cell"></td>
      <td class="cell"></td>
      <td class="cell"></td>
    </tr>
    <tr>
      <td class="cell"></td>
      <td class="cell"></td>
      <td class="cell"></td>
    </tr>
  </table>
  <div class="winner-text"></div>
  
  <script>
    // matriz para manter o estado atual do tabuleiro
    let board = [
      ['', '', ''],
      ['', '', ''],
      ['', '', '']
    ];
    
    // variável para manter o jogador atual (inicia com 'X')
    let currentPlayer = 'X';
    
    // função para alternar o jogador atual
    function togglePlayer() {
      if (currentPlayer === 'X') {
        currentPlayer = 'O';
      } else {
        currentPlayer = 'X';
      }
    }
    
    // função para verificar se há um vencedor
    function checkWinner() {
      // verifica as linhas
      for (let i = 0; i < 3; i++) {
        if (board[i][0] !== '' && board[i][0] === board[i][1] && board[i][1] === board[i][2]) {
          return board[i][0];
        }
      }
      
      // verifica as colunas
      for (let i = 0; i < 3; i++) {
        if (board[0][i] !== '' && board[0][i] === board[1][i] && board[1][i] === board[2][i]) {
          return board[0][i];
        }
      }
      
      // verifica as diagonais
      if (board[0][0] !== '' && board[0][0] === board[1][1] && board[1][1] === board[2][2]) {
        return board[0][0];
      }
      if (board[0][2] !== '' && board[0][2] === board[1][1] && board[1][1] === board[
