# Agentes Inteligentes com Estados

## Descrição

Foi implementado um sistema de agentes inteligentes baseados em estados para os bots da partida.

Cada bot deixa de executar sempre o mesmo comportamento e passa a alternar entre diferentes estados de ação, escolhidos de acordo com a situação atual da partida.

## Funcionamento

A cada ciclo do jogo, o agente percebe o ambiente ao seu redor, observando:

- sua vida atual;
- inimigos visíveis e a distância até eles;
- sua posição em relação à zona segura;
- caixas de itens disponíveis na arena.

Com base nessa percepção, o agente define em qual estado deve atuar e executa o comportamento correspondente.

## Estados implementados

### PATRULHAR

Estado padrão do agente quando não há ameaças nem objetivos relevantes.

Comportamento:
- escolhe um ponto aleatório válido da arena;
- desloca-se até ele;
- ao chegar, seleciona um novo ponto de patrulha.

### ATACAR

Ativado quando existe um inimigo visível e em condições favoráveis de combate.

Comportamento:
- aproxima-se do alvo quando está longe ou sem visão;
- recua quando o inimigo está perto demais;
- desloca-se lateralmente (reposicionamento) durante a troca de tiros;
- atira quando possui visão limpa do alvo.

### FUGIR

Ativado quando o agente está com pouca vida ou em desvantagem no combate.

Comportamento:
- move-se na direção oposta ao inimigo;
- recebe um bônus de velocidade durante a fuga.

### BUSCAR_CAIXA

Ativado quando existe uma caixa de item vantajosa por perto, com prioridade para caixas de vida quando o agente está ferido.

Comportamento:
- desloca-se até a caixa escolhida;
- coleta o item ao alcançá-la.

### VOLTAR_ZONA

Ativado quando o agente está fora (ou próximo do limite) da zona segura.

Comportamento:
- desloca-se em direção ao centro da arena;
- quanto mais distante da zona, maior a urgência do retorno.

## Transições entre estados

O agente reavalia sua situação continuamente, permitindo transições como:

- PATRULHAR → ATACAR, ao avistar um inimigo;
- ATACAR → FUGIR, ao ficar com pouca vida ou em desvantagem;
- FUGIR → BUSCAR_CAIXA, ao encontrar uma caixa de vida próxima;
- qualquer estado → VOLTAR_ZONA, ao ficar fora da área segura;
- ATACAR/FUGIR → PATRULHAR, ao perder o alvo de vista.

## Resultado

Com essa melhoria, os bots passam a se comportar como agentes inteligentes: percebem o ambiente, alternam entre ações distintas e reagem à situação da partida, em vez de agir sempre da mesma forma.
