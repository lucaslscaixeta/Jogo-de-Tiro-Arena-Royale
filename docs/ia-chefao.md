# IA Estratégica do Chefão

## Descrição

Foi implementado um sistema de tomada de decisão para o chefe do modo Boss,
substituindo a escolha aleatória de ataques por uma seleção baseada no estado
atual da partida.

## Funcionamento

O chefe analisa informações do combate:

- distância até o jogador;
- quantidade de jogadores próximos;
- porcentagem de vida restante.

Com essas informações, o agente escolhe qual comportamento executar.

## Estados implementados

### Estado 0 - Ataque à distância

Utilizado quando o jogador está longe.

Comportamento:
- mantém distância;
- dispara projéteis contra o jogador.

### Estado 1 - Ataque corpo a corpo

Utilizado quando o jogador está próximo.

Comportamento:
- aproxima-se do jogador;
- executa ataque de espada em área.

### Estado 2 - Ataque em área

Utilizado quando existem vários jogadores próximos.

Comportamento:
- dispara ataque explosivo;
- tenta atingir múltiplos inimigos.

### Estado 3 - Modo agressivo

Ativado quando o chefe possui pouca vida.

Comportamento:
- aumenta a pressão no combate;
- realiza ataques mais frequentes.

## Regras de decisão

O chefe escolhe seu comportamento seguindo:

- Vida abaixo de 30% → modo agressivo;
- Jogador próximo → ataque corpo a corpo;
- Vários jogadores próximos → ataque em área;
- Jogador distante → ataque à distância.

## Resultado

A melhoria transforma o chefe em um agente inteligente,
pois suas ações deixam de ser aleatórias e passam a considerar
o estado atual da partida.