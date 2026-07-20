# Jogo de Tiro: Arena Royale

Projeto desenvolvido para a disciplina de Inteligência Artificial com o objetivo de aprimorar o comportamento dos agentes do jogo por meio de técnicas clássicas de IA. As melhorias implementadas incluem máquinas de estados finitos (FSM), heurísticas de tomada de decisão, busca de caminho utilizando o algoritmo A* e um sistema de inteligência para o Chefão (Titã).

## Integrantes

| Nome | Matrícula |
|------|-----------|
| Adryan Martins | 24.1.8072 |
| Lucas Lucio | 24.1.8065 |
| Mateus Serretti | 24.1.8060 |

## Melhorias implementadas

### Agentes inteligentes com Máquina de Estados Finitos (FSM)

Os bots passaram a utilizar uma Máquina de Estados Finitos (Finite State Machine - FSM) para organizar seus comportamentos. Cada estado representa uma ação específica, permitindo que os agentes alterem seu comportamento de acordo com a situação da partida.

Estados implementados:

- Patrulhar a arena;
- Perseguir inimigos;
- Atacar;
- Fugir quando a vida estiver baixa;
- Buscar caixas de vida;
- Retornar para a zona segura.

As transições entre estados ocorrem automaticamente com base nas informações do ambiente, proporcionando um comportamento mais natural e organizado.

---

### Heurística para tomada de decisão

Para definir qual estado deve ser executado, foi implementada uma heurística responsável por avaliar continuamente a situação do jogo.

Cada bot considera fatores como:

- Vida atual;
- Distância até os inimigos;
- Distância até caixas de vida;
- Distância da zona segura;
- Presença de obstáculos.

Com base nessas informações, o agente escolhe a ação mais adequada para o momento da partida. Dessa forma, os bots deixam de executar comportamentos fixos e passam a adaptar suas decisões dinamicamente conforme o contexto do jogo.

---

### Busca de caminho com A* (Pathfinding)

Durante os testes foi observado que os bots frequentemente ficavam presos em paredes, cantos e limites da arena. Para solucionar esse problema, foi implementado um sistema de navegação utilizando o algoritmo A*.

A arena foi dividida em uma grade de navegação composta por células livres e bloqueadas. O algoritmo calcula o menor caminho entre a posição atual do agente e seu objetivo, permitindo movimentação em oito direções e evitando cortes diagonais por obstáculos.

Além disso:

- O cálculo considera o tamanho de cada personagem;
- Bots comuns e o Chefão utilizam grades de navegação distintas;
- Caminhos são suavizados para reduzir movimentos desnecessários;
- Destinos inacessíveis são substituídos pelo ponto válido mais próximo;
- Um sistema detecta travamentos e recalcula automaticamente a rota.

Com essa melhoria, os agentes passaram a contornar obstáculos corretamente e reduzir significativamente problemas de movimentação.

---

### Chefão inteligente (Titã)

O comportamento do Chefão foi aprimorado com a implementação de um sistema de tomada de decisão baseado em ameaça e memória.

Sempre que recebe dano, o Titã registra informações sobre cada atacante, incluindo:

- Pontuação de ameaça;
- Dano total causado;
- Quantidade de acertos;
- Último momento em que recebeu dano.

Essas informações são utilizadas para construir um ranking de ameaças, permitindo que o Titã priorize os adversários que mais impactam o combate.

Também foi implementado um sistema de memória de perseguição. Quando o alvo deixa de estar visível, o Titã registra sua última posição conhecida e continua investigando a região em vez de abandonar imediatamente a perseguição.

Durante a perseguição, o Titã utiliza:

- A* para contornar obstáculos;
- Mira preditiva para antecipar o movimento dos adversários;
- Reavaliação periódica do alvo prioritário.

Essas melhorias tornam o comportamento do Chefão mais estratégico, persistente e desafiador.

---

## Tecnologias utilizadas

- HTML5
- CSS3
- JavaScript
- Canvas API

---

## Como executar

Clone o repositório:

```bash
git clone https://github.com/SEU-USUARIO/Jogo-de-Tiro-Arena-Royale.git
```

Entre na pasta do projeto:

```bash
cd Jogo-de-Tiro-Arena-Royale
```

Abra o arquivo `jogodetiro.html` em qualquer navegador moderno.

Não é necessário instalar dependências.

---

## Estrutura da IA

```text
Bot
│
├── Heurística
│
├── Máquina de Estados (FSM)
│
├── Definição do objetivo
│
└── A* Pathfinding
        │
        ▼
    Movimentação
```

---

## Licença

Projeto desenvolvido exclusivamente para fins acadêmicos.
