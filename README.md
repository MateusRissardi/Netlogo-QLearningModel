# Cliff Walking Model com Q-Learning no NetLogo

Este repositório contém uma implementação do clássico problema de *Cliff Walking* (Caminhada no Penhasco) utilizando o algoritmo de Aprendizado por Reforço **Q-Learning**, desenvolvido na plataforma **NetLogo**.

## 🎯 Objetivo

O principal objetivo deste projeto é demonstrar a capacidade de integração de algoritmos de **Aprendizado por Reforço (Reinforcement Learning)** dentro do NetLogo. Ele serve como uma prova de conceito de que é possível sofisticar o comportamento e a tomada de decisão dos agentes (turtles) para além de regras simples baseadas em "se/então", permitindo que eles aprendam com o ambiente através de tentativa e erro.

## ⚙️ Como Funciona

O modelo simula um ambiente de grade (grid world) onde um agente deve navegar de um ponto inicial até um objetivo, evitando cair em um "penhasco".

### O Ambiente
* **Área Segura (Branco):** O agente pode transitar livremente. Cada passo custa **-1** (recompensa negativa) para incentivar o caminho mais curto.
* **Penhasco (Vermelho):** Se o agente pisar aqui, ele recebe uma penalidade severa de **-10** e é enviado de volta ao início.
* **Objetivo (Verde):** Ao alcançar este ponto, o agente recebe uma recompensa de **+10**.

### O Algoritmo (Q-Learning)
O agente não conhece as regras do mapa inicialmente. Ele utiliza uma **Q-Table** para armazenar o valor esperado (utilidade) de realizar cada ação (Cima, Baixo, Esquerda, Direita) em cada estado (patch).

A atualização do conhecimento acontece a cada passo seguindo a equação de Bellman:

$$Q(s,a) \leftarrow Q(s,a) + \alpha [R + \gamma \max Q(s',a') - Q(s,a)]$$

Onde:
* **$\alpha$ (alpha):** Taxa de aprendizado (`learnrate`).
* **$\gamma$ (gamma):** Fator de desconto (`disctax`).
* **$R$:** Recompensa imediata (`reward`).

### Estratégia de Decisão ($\epsilon$-Greedy)
O agente utiliza uma estratégia **Epsilon-Greedy** para balancear entre:
1.  **Exploração (Exploration):** Tentar uma ação aleatória para descobrir novos caminhos (controlado pela variável `exprob`).
2.  **Aproveitamento (Exploitation):** Escolher a melhor ação conhecida até o momento baseada na Q-Table.

## 🚀 Como Usar

### Pré-requisitos
* [NetLogo 6.x](https://ccl.northwestern.edu/netlogo/) instalado.

### Executando o Modelo
1.  Baixe o arquivo `CliffWalkingModel-QLearning.nlogo` deste repositório.
2.  Abra o arquivo no NetLogo.
3.  Clique no botão **Setup** para inicializar o ambiente e as variáveis.
4.  Clique no botão **Go** para iniciar a simulação.

### Parâmetros (Variáveis Globais)
No código (`setup-valores`), você pode ajustar os hiperparâmetros do aprendizado:
* `exprob`: Probabilidade de exploração (inicialmente 25%).
* `learnrate`: Taxa de aprendizado (inicialmente 0.2).
* `disctax`: Fator de desconto para recompensas futuras (inicialmente 0.1).

## 📊 O Que Observar

Ao rodar o modelo, note que:
1.  No início, o agente ("turtle" vermelha) se move erraticamente, caindo frequentemente na zona vermelha.
2.  Com o passar do tempo (ticks), a `totalreward` tende a aumentar.
3.  Eventualmente, o agente aprende o caminho "ótimo" ou "seguro" até a zona verde, demonstrando a convergência do algoritmo Q-Learning.

## 🛠 Tecnologias

* **Linguagem:** NetLogo
* **Conceitos:** Inteligência Artificial, Aprendizado por Reforço, Q-Learning.

## 📝 Licença

Este projeto é de código aberto. Sinta-se à vontade para contribuir ou modificar para fins educacionais.
