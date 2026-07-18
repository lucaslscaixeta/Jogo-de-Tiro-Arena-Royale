# Função Heurística para Decisão dos Bots

## Descrição

Foi implementada uma função heurística para melhorar a tomada de decisão dos bots durante a partida.

A IA passou a avaliar o estado atual do ambiente e atribuir pontuações para diferentes ações possíveis, escolhendo aquela que apresenta maior benefício naquele momento.

## Funcionamento

A função de avaliação considera informações como:

- quantidade de vida atual do bot;
- distância até inimigos;
- vantagem ou desvantagem no combate;
- posição em relação à zona segura;
- disponibilidade e distância de caixas de itens.

Após analisar essas informações, cada ação recebe uma pontuação e o bot executa a ação com maior prioridade.

## Ações avaliadas

### Buscar caixa

Prioridade aumentada quando:

- o bot está com pouca vida;
- existe uma caixa de vida próxima;
- o item pode trazer vantagem durante o combate.

### Voltar para a zona segura

Prioridade aumentada quando:

- o bot está fora da área segura;
- quanto maior a distância da zona, maior a prioridade de retorno.

### Atacar

Prioridade aumentada quando:

- existe um inimigo próximo;
- o inimigo possui pouca vida;
- o bot possui vantagem de combate.

### Fugir

Prioridade aumentada quando:

- o bot está com pouca vida;
- possui desvantagem contra o inimigo;
- existem vários inimigos próximos.

### Patrulhar

Comportamento padrão utilizado quando nenhuma ação possui prioridade suficiente.

## Modelo de decisão

A escolha da ação segue o fluxo:

1. Analisar o estado atual da partida;
2. Calcular a pontuação de cada ação possível;
3. Comparar os valores obtidos;
4. Executar a ação com maior pontuação.

## Resultado

Com essa melhoria, os bots deixam de seguir comportamentos fixos e passam a tomar decisões baseadas na avaliação do ambiente.

A implementação utiliza uma abordagem heurística de avaliação de estados, permitindo que os agentes adaptem seu comportamento conforme as condições da partida.