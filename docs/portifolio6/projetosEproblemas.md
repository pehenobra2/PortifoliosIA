# Algoritmos de Aprendizado de máquina

Ao longo deste documento, foram discutidos diversos algoritmos representativos para cada tipo de aprendizado de máquina: supervisionado, não supervisionado e por reforço. No entanto, o universo de algoritmos de aprendizado de máquina é extenso, e há muitas outras técnicas relevantes. Nesta seção, serão explorados novos algoritmos para cada tipo de aprendizado, oferecendo uma visão mais abrangente das possibilidades disponíveis no campo.

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

---

### **Código em Python**  
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
2. Definição do kernel: Usamos o kernel RBF multiplicado por uma constante. Isso permite que o modelo ajuste a variância e a suavidade da curva.
3. Treinamento: Ajustamos o `GaussianProcessRegressor` aos dados.
4. Predição: Fazemos previsões em novos pontos e obtemos o desvio padrão da incerteza.
5. Visualização: Geramos um gráfico com:
    - Pontos vermelhos representando os dados de treino.
    - Linha azul mostrando a predição do GP.
    - Sombra azul representando a incerteza do modelo (intervalo de confiança de 95%).

### Resultado

![image](https://github.com/user-attachments/assets/5647a620-5e6d-4803-bdf0-445679d97715)


Essa imagem representa a regressão com Processo Gaussiano (GP) aplicada a um conjunto de dados ruidoso. Vamos analisar os elementos principais do gráfico:

1. **Dados de Treinamento (pontos vermelhos)
2. Função Real (linha vermelha tracejada)
3. Previsão do GP (linha azul sólida)
4. Intervalo de Confiança (faixa azul clara)


---

## Algoritmo de Aprendizado não supervisionado; 

## Algoritmo de Aprendizado por reforço. 
