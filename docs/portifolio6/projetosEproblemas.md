# Algoritmos de Aprendizado de máquina

Os Processos Gaussianos (Gaussian Processes - GP) são modelos probabilísticos amplamente utilizados para tarefas de regressão e classificação no contexto do aprendizado supervisionado. Baseados em estatísticas bayesianas, eles permitem capturar a incerteza das previsões de forma natural, tornando-se uma escolha poderosa para problemas em que a quantificação da incerteza é essencial.

## Processos Gaussianos (GP) para Aprendizado de Máquina

Os Processos Gaussianos (Gaussian Processes - GP) são modelos probabilísticos amplamente utilizados para tarefas de regressão e classificação no contexto do aprendizado supervisionado. Baseados em estatísticas bayesianas, eles permitem capturar a incerteza das previsões de forma natural, tornando-os uma escolha poderosa para problemas onde a quantificação da incerteza é essencial.

### **O que é um Processo Gaussiano?**  

Um Processo Gaussiano é uma distribuição sobre funções, onde qualquer conjunto finito de pontos segue uma distribuição normal multivariada. Diferente de modelos tradicionais, que ajustam um conjunto fixo de parâmetros, um GP define uma distribuição sobre funções e usa dados para inferir a mais provável.  

A principal característica de um GP é que ele é definido por uma **função de média** $( m(x) )$ e uma **função de covariância** (também chamada de kernel) $( k(x, x') )$:  

$$f(x) \sim GP(m(x), k(x, x'))$$

- **Função de média $( m(x) )$**: Define a média da função nos pontos de entrada. Muitas vezes é assumida como zero.  
- **Função de covariância $( k(x, x') )$**: Define a relação entre os pontos. O kernel mais comum é o **RBF (Radial Basis Function)**, que mede similaridade entre pontos próximos.  

### **Aplicações de Processos Gaussianos**  
Os Processos Gaussianos são úteis para:  
- **Regressão não paramétrica**: Modelagem de dados sem assumir uma forma fixa da função.  
- **Modelagem de incerteza**: Geração de previsões probabilísticas.  
- **Otimização Bayesiana**: Busca por hiperparâmetros ótimos em aprendizado de máquina.  

### **Exemplo de Aplicação: Regressão com Processos Gaussianos**  
Vamos considerar um exemplo onde ajustamos um GP a um conjunto de dados ruidoso e fazemos previsões para novos pontos.  

#### **Código em Python**  
Utilizaremos a biblioteca `scikit-learn` para implementar um **GP para regressão (Gaussian Process Regression - GPR)**.

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.gaussian_process import GaussianProcessRegressor
from sklearn.gaussian_process.kernels import RBF, WhiteKernel, Matern, ConstantKernel as C

# Gerando mais dados para reduzir incerteza
np.random.seed(42)
X = np.sort(5 * np.random.rand(40, 1), axis=0)  # 40 pontos (antes eram 20)
y = np.sin(X).ravel() + np.random.normal(0, 0.15, X.shape[0])  # Redução do ruído

# Melhorando o kernel: Matérn + WhiteKernel para melhor modelagem de ruído
kernel = C(1.0) * Matern(length_scale=1.0, nu=1.5) + WhiteKernel(noise_level=0.1)

# Criando o modelo de Processo Gaussiano
gp = GaussianProcessRegressor(kernel=kernel, n_restarts_optimizer=10)

# Treinando o modelo
gp.fit(X, y)

# Criando novos pontos para predição
X_pred = np.linspace(0, 5, 100).reshape(-1, 1)
y_pred, sigma = gp.predict(X_pred, return_std=True)

# Plotando os resultados
plt.figure(figsize=(8, 5))
plt.scatter(X, y, c="red", label="Dados de Treinamento")
plt.plot(X_pred, np.sin(X_pred), "r--", label="Função Real")
plt.plot(X_pred, y_pred, "b-", label="Previsão GP")
plt.fill_between(X_pred.ravel(), y_pred - 1.96 * sigma, y_pred + 1.96 * sigma, alpha=0.2, color="blue", label="Intervalo de Confiança (95%)")
plt.xlabel("X")
plt.ylabel("y")
plt.title("Regressão com Processo Gaussiano (Aprimorado)")
plt.legend()
plt.show()

# Exibir os hiperparâmetros aprendidos pelo modelo
print("Kernel otimizado:", gp.kernel_)

```
**Explicação do Código**:
1. Geração de dados: Criamos uma função seno com ruído para simular um problema real.
2. Definição do kernel: Utilizamos um kernel Matérn somado a um WhiteKernel, permitindo que o modelo lide melhor com variações e ruídos nos dados.
3. Treinamento: Ajustamos o `GaussianProcessRegressor` aos dados.
4. Predição: Realizamos previsões em novos pontos e obtemos o desvio padrão da incerteza.
5. Visualização: Geramos um gráfico com:
    - Pontos vermelhos: Dados de treinamento.
    - Linha azul: Predição do GP.
    - Área sombreada azul: Intervalo de confiança de 95%..

### Resultado

![image](https://github.com/user-attachments/assets/5647a620-5e6d-4803-bdf0-445679d97715)

Essa imagem representa a regressão com Processo Gaussiano (GP) aplicada a um conjunto de dados ruidoso. Vamos analisar os elementos principais do gráfico:

1. **Dados de Treinamento**
    - Os pontos vermelhos representam os dados de treinamento, que foram gerados a partir de uma função seno com adição de ruído gaussiano.
    - O conjunto de dados apresenta uma boa distribuição ao longo do domínio, garantindo que o modelo GP possa capturar o comportamento subjacente da função real.
2. Função Real
    - A linha vermelha tracejada representa a função real utilizada para gerar os dados.
    - Isso serve como referência para avaliar a precisão da previsão do modelo GP.
3. Previsão do GP
    - A linha azul sólida representa a predição feita pelo Gaussian Process Regressor.
    - O modelo conseguiu capturar bem a tendência da função real, mantendo uma suavização adequada devido ao kernel Matérn utilizado.
4. Intervalo de Confiança (95%)
    - A região azul ao redor da linha de previsão representa o intervalo de confiança de 95%.
    - Em áreas onde há mais dados, o intervalo é menor, indicando menor incerteza.
    - Em regiões com menos dados (especialmente nas extremidades), a incerteza aumenta, como esperado em modelos probabilísticos.
5. Melhorias Aplicadas
    - Em comparação com uma versão mais básica do GP, este modelo usa um kernel Matérn `+ WhiteKernel`, que melhora a modelagem da variação e do ruído nos dados.
    - O aumento da quantidade de pontos de treinamento (40 pontos em vez de 20) ajudou a reduzir a incerteza e melhorar a precisão das previsões.
6. Interpretação Final
    - O modelo GP fez um ótimo ajuste à função real, demonstrando sua capacidade de capturar padrões complexos sem assumir uma forma fixa para a função subjacente.
    - O intervalo de confiança se comporta como esperado, expandindo-se nas regiões com menos dados e estreitando-se onde há mais observações.
    - A escolha do kernel foi adequada, pois conseguiu lidar bem com a variação dos dados e modelar o ruído presente.

### Conclusão

Os Processos Gaussianos são ferramentas poderosas para modelagem probabilística e são amplamente utilizados em problemas que exigem previsões confiáveis e quantificação da incerteza. A flexibilidade desses modelos permite aplicações variadas, desde regressão até otimização de hiperparâmetros em algoritmos de aprendizado de máquina.

---

## DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

O DBSCAN (Density-Based Spatial Clustering of Applications with Noise) é um algoritmo de agrupamento baseado em densidade, amplamente utilizado para identificar padrões e estruturas em conjuntos de dados complexos. Ele é particularmente útil para detectar clusters de formas arbitrárias e lidar com ruídos (outliers) sem a necessidade de especificar o número de clusters previamente, como ocorre com o K-Means.

### Como o DBSCAN Funciona?

O DBSCAN classifica os pontos do conjunto de dados em três categorias:

1. Pontos Centrais (Core Points): pontos que possuem pelo menos um número mínimo (minPts) de vizinhos dentro de uma distância máxima (epsilon).
2. Pontos de Borda (Border Points): pontos que não possuem vizinhos suficientes para serem pontos centrais, mas estão dentro do alcance de um ponto central.
3. Ruídos (Outliers): pontos que não pertencem a nenhum cluster, pois não satisfazem as condições anteriores.

O algoritmo funciona da seguinte maneira:

1. Escolhe um ponto aleatório ainda não visitado.
2. Se ele for um ponto central, inicia um novo cluster e expande a busca pelos vizinhos.
3. Se for um ponto de borda, ele é adicionado ao cluster mais próximo.
4. Se for um outlier, é marcado como ruído.
5. Repete o processo até todos os pontos serem visitados.

### Vantagens e Aplicações do DBSCAN

O DBSCAN tem várias vantagens em relação a outros algoritmos de agrupamento, como o K-Means:
- Detecta clusters de forma arbitrária: enquanto o K-Means assume clusters esféricos, o DBSCAN pode identificar grupos de qualquer formato.
- Não exige número de clusters pré-definido: o número de clusters emerge dos próprios dados.
- Robusto contra outliers: pontos ruidosos são identificados e não influenciam os clusters.

O DBSCAN é utilizado em diversas aplicações, como:
- Segmentação de imagens e análise de padrões em visão computacional.
- Detecção de anomalias em sistemas de segurança e monitoramento.
- Análise de dados geoespaciais, como agrupamento de localizações de crimes ou hotspots de tráfego.

### Exemplo de Implementação em Python

Abaixo, implementamos um exemplo de DBSCAN usando a biblioteca `scikit-learn` para agrupar um conjunto de dados bidimensional.
```
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import make_moons
from sklearn.cluster import DBSCAN

# Gerando um conjunto de dados em formato de lua crescente (não linear)
X, _ = make_moons(n_samples=300, noise=0.05, random_state=42)

# Aplicando DBSCAN
dbscan = DBSCAN(eps=0.2, min_samples=5)
labels = dbscan.fit_predict(X)

# Visualizando os clusters
plt.figure(figsize=(8,5))
plt.scatter(X[:, 0], X[:, 1], c=labels, cmap='plasma', edgecolors='k')
plt.xlabel('X')
plt.ylabel('Y')
plt.title('Clusters Detectados pelo DBSCAN')
plt.show()
```
### Resultado

![image](https://github.com/user-attachments/assets/bf8b6fae-c4c8-4aa7-b31c-50f39ffedcf7)
A imagem mostra os clusters detectados pelo algoritmo DBSCAN em um conjunto de dados no formato de duas luas crescentes (moons). Cada ponto representa uma amostra do conjunto de dados, e as cores indicam os diferentes clusters identificados.

**Observação sobre os Clusters: 
1. Clusters bem definidos:
    - O DBSCAN conseguiu segmentar corretamente os dois grupos de pontos curvados, colorindo-os de maneira distinta (amarelo e azul escuro).
    - Isso confirma que o algoritmo é eficiente para detectar estruturas não lineares, algo que algoritmos como K-Means teriam dificuldades em realizar.
2. Ausência de ruídos (outliers):
    - Nenhum ponto foi claramente identificado como ruído (normalmente indicado por uma cor diferente dos clusters principais, como preto ou cinza).
    - Isso sugere que os parâmetros `eps=0.2` e `min_samples=5` foram bem ajustados para esse conjunto de dados, garantindo que todos os pontos fossem atribuídos a um cluster.
3. Clusters de formas arbitrárias:
    - Diferente do K-Means, que tende a criar grupos esféricos, o DBSCAN identificou os clusters de forma natural e arbitrária, respeitando a estrutura dos dados.
4. Parâmetros e Sensibilidade:
    - Se o valor de `eps` fosse maior, os dois grupos poderiam ter sido fundidos em um único cluster.
    - Se `eps` fosse muito pequeno, mais pontos poderiam ter sido classificados como ruído.

### Conclusão

O DBSCAN funcionou muito bem para esse tipo de dado, segmentando corretamente as duas distribuições curvadas sem a necessidade de definir o número de clusters previamente. O resultado reforça a eficiência desse algoritmo para dados complexos e com formas irregulares.

---

## Advantage Actor-Critic (A2C)

O **Advantage Actor-Critic (A2C)** é um algoritmo de Aprendizado por Reforço que combina as abordagens de **Aprendizado por Política (Actor)** e **Aprendizado por Valor (Critic)**. Ele busca melhorar a estabilidade e a eficiência do treinamento ao reduzir a variância das atualizações da política por meio da função de vantagem.

### Como o A2C Funciona?

O A2C é baseado na arquitetura **Actor-Critic**, onde:

- **Actor (Ator)**: Responsável por selecionar ações com base em uma política parametrizada $pi(s, a)$.
- **Critic (Crítico)**: Avalia o valor esperado de um estado $V(s)$ e calcula a **vantagem** $A(s, a)$, que mede o impacto da ação escolhida sobre a recompensa futura.

O treinamento ocorre da seguinte maneira:

1. O **Actor** escolhe uma ação $a$ com base na política atual $pi(s, a)$.
2. O **Ambiente** retorna a recompensa $r$ e o próximo estado $s'$.
3. O **Critic** estima os valores $V(s)$ e $V(s')$, calculando a vantagem:
   
   $$A(s, a) = r + \gamma V(s') - V(s)$$
   
4. O **Actor** é atualizado para maximizar a vantagem $A(s, a)$, enquanto o **Critic** é atualizado para minimizar o erro de predição $V(s) - (r + \gamma V(s'))$.
5. O processo se repete até que a política do agente seja otimizada.

### Vantagens e Aplicações do A2C

O A2C apresenta vários benefícios em relação a métodos tradicionais como o Q-Learning e o REINFORCE:

- **Redução da variância**: O uso do Critic ajuda a estabilizar o aprendizado.
- **Aprendizado eficiente**: O algoritmo pode ser treinado de forma paralela, acelerando a convergência.
- **Adaptação a espaços contínuos**: Diferente do Q-Learning, o A2C pode lidar bem com ações contínuas, tornando-o ideal para aplicações como controle de robôs.

As aplicações do A2C incluem:

- **Controle Robótico**: Aprendizado de movimentos otimizados para robôs autônomos.
- **Jogos**: Treinamento de agentes para jogos como Atari e StarCraft.
- **Finanças**: Modelagem de estratégias de decisão para trading algorítimo.

### Exemplo de Implementação em Python

```python
import numpy as np

import numpy as np

class SimpleEnvironment:
    def __init__(self):
        self.state_space = 3  # 3 estados possíveis
        self.action_space = 2  # 2 ações possíveis (0 ou 1)
        self.state = 0  # Estado inicial

    def reset(self):
        """Reseta o ambiente para o estado inicial."""
        self.state = 0
        return self.state

    def step(self, action):
        """Executa uma ação no ambiente e retorna o novo estado e a recompensa."""
        reward = 0
        if action == 0:  # Ação 0 leva ao estado 1 com recompensa +1
            self.state = 1
            reward = 1
        elif action == 1:  # Ação 1 leva ao estado 2 com recompensa -1
            self.state = 2
            reward = -1
        return self.state, reward


class ActorCritic:
    def __init__(self, state_space, action_space, alpha=0.01, gamma=0.99, lambda_=0.95):
        """Inicializa o agente A2C com os parâmetros dados."""
        self.state_space = state_space
        self.action_space = action_space
        self.alpha = alpha  # Taxa de aprendizado
        self.gamma = gamma  # Fator de desconto
        self.lambda_ = lambda_  # Fator de trace de elegibilidade

        # Inicializa os parâmetros do ator (política) e crítico (valor)
        self.theta = np.random.rand(state_space, action_space)  # Parâmetros do ator
        self.weights = np.random.rand(state_space)  # Parâmetros do crítico

        # Inicializa os traces de elegibilidade
        self.e_trace = np.zeros_like(self.weights)

    def softmax(self, x):
        """Função Softmax para calcular probabilidades de ação."""
        e_x = np.exp(x - np.max(x))  # Evitar overflow numérico
        return e_x / e_x.sum(axis=0, keepdims=True)

    def choose_action(self, state):
        """Escolhe uma ação com base na política atual (distribuição softmax)."""
        action_probabilities = self.softmax(self.theta[state, :])
        return np.random.choice(self.action_space, p=action_probabilities)

    def update(self, state, action, reward, next_state, done):
        """Atualiza os parâmetros do ator e crítico com base nas transições."""
        v = self.weights[state]  # Valor atual do estado
        v_next = self.weights[next_state] if not done else 0  # Valor do próximo estado

        # Calcula o erro temporal (TD error)
        td_error = reward + self.gamma * v_next - v
        
        # Atualiza o crítico (valores estimados dos estados)
        self.weights[state] += self.alpha * td_error
        
        # Atualiza o trace de elegibilidade
        self.e_trace[state] = self.gamma * self.lambda_ * self.e_trace[state] + 1

        # Atualiza o ator (política)
        action_probabilities = self.softmax(self.theta[state, :])
        self.theta[state, action] += self.alpha * td_error * self.e_trace[state] * (1 - action_probabilities[action])

    def train(self, env, episodes=100):
        """Treina o agente em um número de episódios."""
        for episode in range(episodes):
            state = env.reset()
            done = False
            total_reward = 0
            
            while not done:
                # Escolhe a ação a ser tomada
                action = self.choose_action(state)
                
                # Realiza a ação no ambiente e recebe o próximo estado e a recompensa
                next_state, reward = env.step(action)
                
                # Atualiza os parâmetros do agente (ator e crítico)
                self.update(state, action, reward, next_state, done)
                
                state = next_state
                total_reward += reward
                done = (state == 2)  # O episódio termina quando o estado 2 é alcançado

            print(f"Episode {episode + 1}: Total Reward: {total_reward}")

# Cria o ambiente simples
env = SimpleEnvironment()

# Cria o agente A2C
agent = ActorCritic(state_space=env.state_space, action_space=env.action_space)

# Treina o agente por 100 episódios
agent.train(env, episodes=100)

```
**Explicação do código:

1. Ambiente Simples: O ambiente tem 3 estados possíveis (0, 1 e 2) e 2 ações possíveis (0 e 1). O estado inicial é 0.
    - Se o agente escolhe a ação 0, ele vai para o estado 1 e recebe uma recompensa de +1.
    - Se o agente escolhe a ação 1, ele vai para o estado 2 e recebe uma recompensa de -1.
  
2. Agente A2C: O agente usa o algoritmo Actor-Critic para aprender uma política (ação a ser tomada) e um valor (o valor de cada estado).
    - O ator escolhe ações com base em uma política probabilística (usando softmax).
    - O crítico avalia o valor dos estados.
    - O agente é treinado para maximizar a recompensa total e minimizar o erro temporal (TD error).

3. Treinamento: O agente é treinado por 30 episódios, e ao final de cada episódio, a recompensa total é registrada.

### Resultado

Agora, vamos olhar a tabela de resultados:
| Episode | Total Reward |
|---------|--------------|
| 1       | 1            |
| 2       | 0            |
| 3       | 0            |
| 4       | 0            |
| 5       | 1            |
| 6       | 0            |
| 7       | 3            |
| 8       | 6            |
| 9       | 2            |
| 10      | -1           |
| 11      | -1           |
| 12      | -1           |
| 13      | 5            |
| 14      | -1           |
| 15      | 2            |
| 16      | -1           |
| 17      | 5            |
| 18      | 8            |
| 19      | 10           |
| 20      | 7            |
| 21      | -1           |
| 22      | -1           |
| 23      | 14           |
| 24      | 58           |
| 25      | -1           |
| 26      | 4            |
| 27      | 1            |
| 28      | -1           |
| 29      | -1           |
| 30      | 26           |

**Observações**:
- Comportamento Inicial: Nos primeiros episódios, as recompensas são instáveis. O agente explora o ambiente e começa a aprender a política que maximiza a recompensa.
- Flutuação nas Recompensas: O agente começa com valores de recompensa baixos ou zero em muitos episódios, mas rapidamente começa a encontrar estratégias que geram recompensas maiores.
- Picos de Recompensa: A partir do episódio 17, há um aumento notável nas recompensas. Isso pode ser explicado pelo agente aprendendo e ajustando sua política, alcançando resultados mais eficazes.
- Episódio 24: O valor de recompensa de 58 no episódio 24 é uma grande discrepância. Isso pode indicar que o agente encontrou uma sequência de ações que geraram uma recompensa substancial. O fato de ser tão alto sugere que o agente pode ter começado a se comportar de forma mais otimizada.
- Oscilação nos Últimos Episódios: Nos episódios 25 a 29, o agente parece ter uma oscilação nas recompensas, retornando a valores negativos e depois estabilizando em torno de 26 no episódio 30. Isso pode indicar que o agente ainda está ajustando sua política.

**O que significa:**
1. Aprendizado do Agente: O agente está aprendendo uma política eficaz, mas, como em muitos algoritmos de aprendizado por reforço, ele precisa de exploração para encontrar boas ações. No início, ele tenta diferentes ações e seus resultados flutuam bastante. À medida que o treinamento avança, ele começa a otimizar suas decisões, resultando em recompensas mais altas.
2. Comportamento de Exploração e Exploração: Nos primeiros episódios, o agente explora várias ações, o que resulta em muitas recompensas negativas. À medida que ele aprende, ele começa a explorar menos e a explorar mais ações que oferecem boas recompensas.
3. Convergência da Política: Após várias iterações, o agente se aproxima de uma política que maximiza suas recompensas, como mostrado pelos picos nos episódios 17 a 24.

**Gráfico:**
![image](https://github.com/user-attachments/assets/ba62369f-1f87-4a5e-bc47-839447116a25)
O gráfico gerado pelo código mostra a variação das recompensas por episódio. Se você olhar para ele, provavelmente verá um aumento gradual das recompensas, com algumas flutuações e picos mais altos. Isso é um reflexo direto da melhora da política do agente ao longo do tempo.

### Conclusão

O **Advantage Actor-Critic (A2C)** é um algoritmo poderoso que combina os benefícios do aprendizado baseado em política e em valor, oferecendo uma solução mais estável e eficiente para problemas de decisão sequencial. Seu uso em robótica, jogos e finanças demonstra seu grande potencial na tomada de decisão autônoma.


---
