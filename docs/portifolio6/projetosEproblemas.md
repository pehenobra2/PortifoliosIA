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

---

## Algoritmo de Aprendizado não supervisionado; 

## Algoritmo de Aprendizado por reforço. 
