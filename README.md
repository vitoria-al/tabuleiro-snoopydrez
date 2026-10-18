#  Snoopydrez
O snoopydrez é um jogo de tabuleiro de xadrez desenvolvido com HTML,CSS E JAVASCRIPIT para a disciplina de desenvolvimento web.

## Como executar o projeto?

- Abaixe os arquivos do projeto
- Abra o arquivo em index.html no navegador
- O jogo abrirá no navegador

## Estrutura do projeto

- Index.html, página principal que carrega o tabuleiro
  
  Js/
  
- Board.js, cria o tabuleiro e a matriz
- Game.js, coontrola o funcionamento da partida, as jogas e os turnos
- Pieces.js, atualiza as peças na tela e registra as capturas
- Rules.js, valida a jogada e aplica as regras
- Main.js, conecta tudo e começa o jogo

-Style.css, define cores e tamanhos do tabuleiro e das peças

## Como o estado do tabuleiro é armazenado

- O estado do tabuleiro é armazenado em JavaScript por meio de uma matriz 8x8, que representa as 64 casas do tabuleiro
- Cada posição da matriz guarda um código correspondente à peça que ocupa aquela casa
- As casas vazias são representadas pelo valor `null`
- As peças são identificadas por códigos, como `wP` para peão branco, `bP` para peão preto, `wK` para rei branco e `bK` para rei preto
- A matriz é atualizada sempre que uma peça realiza um movimento válido
- O tabuleiro exibido na tela é atualizado conforme as informações armazenadas na matriz
- A matriz também é utilizada para verificar movimentos válidos, capturas e situações de xeque
- O turno atual é armazenado em uma variável separada, responsável por indicar qual jogador pode realizar a próxima jogada
- A seleção da peça também é armazenada em uma variável, permitindo identificar qual peça o jogador deseja movimentar
- O jogo utiliza essas informações para controlar o andamento da partida e verificar situações de xeque-mate e afogamento

## Como as jogadas são validadas

- O jogo verifica se a peça selecionada pertence ao jogador do turno atual
- Cada peça possui regras próprias de movimentação, que são verificadas antes de permitir uma jogada
- O sistema impede movimentos inválidos, como mover uma peça para uma casa fora do tabuleiro ou desrespeitar seu padrão de movimentação
- O jogo verifica se o caminho está livre para peças como torre, bispo e dama
- O jogador não pode capturar uma peça da mesma cor
- As capturas são permitidas quando a peça adversária está em uma casa que pode ser alcançada por um movimento válido
- O jogo verifica se o movimento não deixa o próprio rei em xeque
- Se houver xeque, a jogada deve eliminar a ameaça ao rei
- O sistema verifica se existem jogadas legais disponíveis para o jogador
- A promoção do peão é realizada quando ele alcança a última fileira do tabuleiro
- Após uma jogada válida, o tabuleiro é atualizado e o turno passa para o outro jogador

## Regras implementadas

### Movimentação das peças conforme o tipo

- **Peão:** movimenta-se uma casa para frente, podendo avançar duas casas em seu primeiro movimento, desde que o caminho esteja livre. Captura peças adversárias uma casa na diagonal para frente e não pode andar para trás

- **Torre:** movimenta-se quantas casas quiser na horizontal ou na vertical, desde que não existam peças bloqueando o caminho

- **Bispo:** movimenta-se quantas casas quiser na diagonal, desde que o caminho esteja livre

- **Cavalo:** movimenta-se em formato de L, avançando duas casas em uma direção e uma casa na direção perpendicular. É a única peça que pode saltar sobre outras peças

- **Dama (Rainha):** movimenta-se quantas casas quiser na horizontal, vertical ou diagonal, desde que o caminho esteja livre

- **Rei:** movimenta-se uma casa por vez em qualquer direção, desde que a casa de destino não esteja ameaçada por uma peça adversária

### Captura de peças

- O jogador pode capturar peças adversárias seguindo as regras de movimentação da peça selecionada
- A peça capturada é retirada do tabuleiro
- As peças capturadas são exibidas na área correspondente ao jogador que realizou a captura
- Não é permitido capturar peças da mesma cor

### Alternância de turnos

- As peças brancas iniciam a partida
- Os jogadores realizam seus movimentos alternadamente
- Cada jogador só pode movimentar as peças de sua própria cor
- Após um movimento válido, o turno passa para o adversário
- O jogo indica na tela qual jogador deve realizar a próxima jogada

### Xeque

- O jogo identifica quando o rei está ameaçado por uma peça adversária
- Quando ocorre um xeque, o jogador precisa realizar uma jogada que elimine a ameaça
- Não é permitido realizar movimentos que deixem o próprio rei em xeque

### Xeque-mate

- O xeque-mate acontece quando o rei está em xeque e não existe nenhuma jogada válida para eliminar a ameaça
- Quando o xeque-mate é identificado, a partida é encerrada
- O jogo apresenta uma mensagem informando qual jogador venceu

### Afogamento

- O afogamento acontece quando o jogador não está em xeque, mas não possui nenhuma jogada válida
- Quando essa situação é identificada, a partida termina empatada
- O resultado do empate é apresentado na tela

### Promoção do peão

- Quando um peão alcança a última fileira do tabuleiro, ele pode ser promovido
- O jogador pode escolher entre dama, torre, bispo ou cavalo
- A peça escolhida substitui o peão no tabuleiro
- A promoção acontece antes da troca de turno

### Bloqueio de movimentos inválidos

- O jogo impede movimentos que desrespeitam as regras do xadrez
- O jogador não pode movimentar uma peça adversária
- O sistema verifica se a casa de destino é válida
- Movimentos que deixariam o próprio rei em xeque são bloqueados
- As casas disponíveis para movimentação são destacadas no tabuleiro

## Funcionalidades extras implementadas

### Histórico de jogadas

- O jogo registra os movimentos realizados durante a partida
- As jogadas ficam disponíveis em uma área de histórico, permitindo acompanhar os movimentos realizados pelos jogadores
- O histórico é atualizado conforme novas jogadas são executadas
- Ao iniciar uma nova partida, o histórico é reiniciado


## Funcionamento da partida

- O tabuleiro possui 8 linhas e 8 colunas, totalizando 64 casas
- As peças são posicionadas conforme a posição inicial oficial do xadrez
- As peças são representadas por imagens SVG
- O jogador pode selecionar e movimentar peças utilizando cliques ou arrastando e soltando
- O jogo destaca a peça selecionada e os movimentos disponíveis
- As jogadas são verificadas antes de serem executadas
- O sistema identifica xeque, xeque-mate e empate por afogamento
- Ao encerrar uma partida, o resultado é apresentado na tela
- O botão de nova partida permite reiniciar o jogo, restaurando o tabuleiro e os turnos
- A interface é responsiva, adaptando-se a diferentes tamanhos de tela
