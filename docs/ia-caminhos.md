# Busca de Caminho com A* para os Bots

## Objetivo

Foi implementado um sistema de busca de caminho utilizando o algoritmo **A\*** (A-Star) para melhorar a movimentação dos bots pela arena. Com essa abordagem, os bots conseguem encontrar rotas até um objetivo desviando das paredes e outros obstáculos do mapa.

Essa melhoria está relacionada ao conteúdo de **resolução de problemas de busca**, utilizando uma estratégia heurística para encontrar caminhos eficientes.

---

## Funcionamento

A navegação é realizada sobre uma **grade (grid)** construída a partir do mapa da arena.

Cada célula da grade pode ser classificada como:

- **Livre:** pode ser utilizada na navegação.
- **Bloqueada:** contém uma parede ou obstáculo e não pode ser atravessada.

Durante a inicialização, a grade é criada e armazenada para reutilização durante a execução do jogo.

---

## Algoritmo A*

O algoritmo recebe:

- posição inicial do bot;
- posição do objetivo;
- raio do bot.

Inicialmente, essas posições são convertidas para células da grade. Em seguida, o algoritmo realiza a busca utilizando:

- custo acumulado (**g**);
- heurística baseada na distância euclidiana (**h**);
- custo total (**f = g + h**).

Os movimentos permitidos são:

- cima;
- baixo;
- esquerda;
- direita;
- diagonais.

Para evitar que o bot atravesse os cantos das paredes, movimentos diagonais somente são permitidos quando as duas células adjacentes também são livres.

Ao encontrar o objetivo, o caminho é reconstruído e armazenado para que o bot percorra cada ponto até chegar ao destino.

---

## Reutilização do caminho

O caminho calculado é armazenado pelo bot e somente é recalculado quando:

- o objetivo muda significativamente;
- o caminho é concluído;
- o caminho fica desatualizado após um intervalo de tempo.

Essa estratégia reduz a quantidade de execuções do algoritmo A*, melhorando o desempenho do jogo.

---

## Utilização pelos bots

A busca de caminho pode ser utilizada em diferentes comportamentos da IA, como:

- perseguir o jogador;
- buscar caixas de vida;
- buscar escudos;
- buscar armas;
- fugir de ameaças;
- retornar para dentro da zona segura.

Independentemente do objetivo, o deslocamento passa a considerar os obstáculos existentes na arena.

---

## Benefícios

A implementação proporciona diversas melhorias na movimentação dos bots:

- navegação inteligente pela arena;
- desvio automático de paredes;
- movimentação mais natural;
- redução de colisões contra obstáculos;
- reutilização dos caminhos para diminuir processamento;
- suporte para diferentes estratégias de comportamento da IA.

---

## Arquivos relacionados

As principais funções implementadas são:

- `construirGradeNavegacao()`
- `obterGradeNavegacao()`
- `buscarCaminhoAStar()`
- `calcularPontoFuga()`
- `moverBotComAStar()`

Essas funções são responsáveis pela construção da grade de navegação, execução do algoritmo A*, definição de pontos de fuga e movimentação dos bots utilizando o caminho encontrado.