# Reinforcement Learning - Projeto Integrado

### Turma – 7DTS
#### Prof. – Felipe Souza Amaral
* 350565 – Emerson Faria de Oliveira
* 349639 – Caio Lima Uno So
* 350614 – Tiago Muniz de Oliveira 
* 349954 – Vinicius Vendrami Scocca 

### Contexto:
Imagine que você está trabalhando em uma empresa de logística que opera uma frota de robôs de entrega autônomos. Sua tarefa é implementar um algoritmo de aprendizado por reforço para otimizar a entrega de pacotes em um ambiente simulado. Os robôs têm a capacidade de se mover em um ambiente em grade 2D e devem aprender a tomar decisões sobre para onde se mover para entregar pacotes de forma eficiente.

### Objetivo:
O objetivo do desafio é implementar um agente de aprendizado por reforço usando ténicas como por exemplo Q-Table, equação de Bellman, ε-greedy e etc, para maximizar o retorno cumulativo ao entregar pacotes no menor tempo possível, considerando um "living penalty" para incentivar o agente a ser eficiente.

### Tarefas:
1.	Modelagem do ambiente: Crie um ambiente 2D simulado, onde o agente pode se mover em um grid. Considere que o ambiente tem obstáculos e pontos de entrega de pacotes.
2.	Definição do MDP: Modele o problema como um MDP, definindo os estados, as ações, as recompensas, a função de transição e o fator de desconto.
3.	Implementação da Q-Table: Crie uma Q-Table para representar o valor estimado de cada par (estado, ação).
4.	Implementação do agente: Desenvolva um agente de aprendizado por reforço que utiliza a equação de Bellman para atualizar a Q-Table com base nas recompensas recebidas ao longo do tempo.
5.	Living Penalty: Introduza um "living penalty" para penalizar o agente por gastar muito tempo no ambiente. Isso deve incentivar o agente a encontrar a rota mais eficiente para entregar os pacotes.
6.	Treinamento e avaliação: Treine o agente usando um algoritmo de aprendizado por reforço, como o Q-Learning, e avalie seu desempenho em termos de eficiência na entrega de pacotes.

### Critérios de Avaliação:
Os alunos serão avaliados com base nos seguintes critérios:
1.	Implementação correta do ambiente, MDP e Q-Table.
2.	Implementação do algoritmo de aprendizado por reforço (Q-Learning ou similar).
3.	Introdução e configuração adequada do "living penalty".
4.	Eficiência do agente na entrega de pacotes.
5.	Documentação clara e código bem comentado em Python.

______________________________________________________________________

## MDP para o Ambiente de Entrega com Agente de Q-Learning

- **Estados**: Cada estado é uma posição na grade 2D, definida por uma tupla \((x, y)\). A grade tem dimensões de 9x9, e os estados excluem posições ocupadas por obstáculos.

- **Ações**: O agente pode tomar uma dentre quatro possíveis ações em cada estado:
  - 0: Mover para cima (\(-1, 0\))
  - 1: Mover para baixo (\(+1, 0\))
  - 2: Mover para a esquerda (\(0, -1\))
  - 3: Mover para a direita (\(0, +1\))

- **Recompensas**: O agente recebe recompensas ou penalidades baseadas em suas ações:
  - Uma recompensa positiva ao alcançar um ponto de entrega.
  - Uma penalidade (recompensa negativa) ao tentar mover para uma célula contendo um obstáculo ou ao tentar sair dos limites da grade.
  - Uma penalidade por viver (\(-0.1\)) é aplicada a cada ação para incentivar o agente a alcançar o objetivo de maneira eficiente.

- **Função de Transição**: A função de transição é determinística para a maioria das ações. O agente se move na direção especificada pela ação, a menos que isso o leve para fora da grade ou para um obstáculo, caso em que o agente permanece no mesmo estado.

- **Fator de Desconto** (\(\gamma\)): O valor do fator de desconto é 0.95, indicando que recompensas futuras são consideradas quase tão importantes quanto recompensas imediatas, mas com uma ligeira depreciação com o tempo.

- **Política de Exploração** (\(\epsilon\)): O valor de \(\epsilon\) é 0.1, significando que há uma probabilidade de 10% de o agente escolher uma ação aleatória, facilitando a exploração do ambiente.

______________________________________________________________________

<video controls src="agent_animation.mp4" title="Title"></video>