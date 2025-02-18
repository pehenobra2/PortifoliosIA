# Aprendizado de Máquina

Aprendizado de Máquina (Machine Learning) é um ramo da Inteligência Artificial que se concentra no desenvolvimento de sistemas capazes de aprender com dados e melhorar seu desempenho ao longo do tempo, sem a necessidade de programação explícita para cada situação. Em vez de depender de um conjunto fixo de regras predefinidas, os modelos de aprendizado de máquina identificam padrões, fazem previsões e ajustam seus resultados conforme recebem novos dados, tornando-se mais precisos e eficientes.

Essa abordagem revolucionou diversas áreas, permitindo que computadores realizem tarefas complexas que antes exigiam intervenção humana. Entre suas aplicações mais comuns, destacam-se o reconhecimento de voz e imagem, sistemas de recomendação personalizados (como os utilizados por plataformas de streaming e e-commerce), detecção de fraudes em transações financeiras e até a condução autônoma de veículos.

O avanço dessa tecnologia tem sido impulsionado pelo crescimento exponencial da capacidade computacional, pelo acesso a grandes volumes de dados e pelo desenvolvimento de algoritmos cada vez mais sofisticados. Com isso, o aprendizado de máquina se tornou uma ferramenta indispensável para a automação de processos, a extração de insights estratégicos e a criação de soluções inovadoras em diversos setores da indústria e da ciência.

---

# Tipos de aprendizados de máquina

O Aprendizado de Máquina pode ser classificado em três principais categorias, dependendo da forma como os dados são utilizados para treinar os modelos: aprendizado supervisionado, aprendizado não supervisionado e aprendizado por reforço. Cada um desses tipos possui características específicas e é aplicado a diferentes problemas.

## Aprendizado supervisionado

No aprendizado supervisionado, o modelo é treinado com um conjunto de dados rotulado, ou seja, cada entrada possui uma saída conhecida. O objetivo é ensinar o modelo a associar corretamente as entradas às saídas, de modo que ele possa fazer previsões precisas quando novos dados forem apresentados.

Esse tipo de aprendizado é amplamente utilizado em problemas de classificação (como a categorização de e-mails em spam e não spam) e regressão (como a previsão do valor de um imóvel com base em suas características). Alguns dos algoritmos mais comuns incluem regressão linear, árvores de decisão, redes neurais e máquinas de vetores de suporte (SVM).

## Aprendizado não supervisionado

Diferente do aprendizado supervisionado, o aprendizado não supervisionado trabalha com dados que não possuem rótulos, ou seja, o modelo precisa identificar padrões, relações ou estruturas nos dados sem qualquer orientação explícita.

Uma das principais aplicações desse tipo de aprendizado é o agrupamento (clustering), onde os algoritmos segmentam os dados em grupos com características semelhantes, como na segmentação de clientes em campanhas de marketing. Além disso, técnicas de aprendizado não supervisionado são usadas para reduzir a dimensionalidade dos dados e identificar anomalias. Algoritmos populares incluem K-Means, DBSCAN e análise de componentes principais (PCA).

## Aprendizado por reforço

No aprendizado por reforço, um agente aprende a tomar decisões interagindo com um ambiente dinâmico e recebendo feedback em forma de recompensas ou penalidades. Esse tipo de aprendizado é baseado na tentativa e erro e tem como objetivo encontrar a melhor sequência de ações para maximizar a recompensa ao longo do tempo.

Essa abordagem é amplamente utilizada em jogos (como o AlphaGo, que superou campeões humanos), robótica (para treinar robôs a realizarem tarefas complexas) e controle de sistemas (como otimização de redes de telecomunicações e tráfego). Algoritmos como Q-Learning, Deep Q-Networks (DQN) e Aprendizado por Reforço Profundo são alguns dos mais utilizados nessa categoria.

---

# Classificação e regressão

De acordo com Hastie, Tibshirani e Friedman (2009), classificação e regressão são tarefas fundamentais no aprendizado de máquina supervisionado, sendo diferenciadas pelo tipo de saída gerada.

A classificação é um problema em que o modelo deve prever um rótulo categórico a partir de um conjunto de dados de entrada. Ou seja, o objetivo é atribuir cada amostra a uma classe predefinida. Um exemplo clássico desse tipo de problema é a identificação de e-mails como spam ou não spam, bem como a categorização de imagens em diferentes classes, como cães e gatos. Os algoritmos mais utilizados para classificação incluem árvores de decisão, máquinas de vetores de suporte (SVM) e redes neurais artificiais.

Já a regressão tem como objetivo prever um valor numérico contínuo com base em variáveis de entrada. Esse tipo de problema é comum em aplicações como a estimativa do preço de imóveis com base em características como metragem, localização e número de quartos, bem como na previsão da temperatura em determinada região. Entre os principais algoritmos de regressão, destacam-se a regressão linear, regressão polinomial e redes neurais profundas (HASTIE; TIBSHIRANI; FRIEDMAN, 2009).

## Extração de características

Para que os modelos de aprendizado de máquina possam interpretar e processar os dados de maneira eficiente, é necessário realizar a extração de características, que consiste em selecionar ou transformar atributos dos dados brutos em representações mais significativas. Segundo Hastie, Tibshirani e Friedman (2009), esse processo é essencial para aumentar a eficiência dos modelos e reduzir a dimensionalidade dos dados.

Uma técnica amplamente utilizada para esse fim é a Análise de Componentes Principais (PCA), que busca encontrar um novo conjunto de variáveis (componentes principais) capazes de representar a maior parte da variabilidade dos dados, reduzindo sua complexidade sem perder informações relevantes. Esse tipo de abordagem é particularmente útil para evitar problemas de sobreajuste e melhorar a performance dos algoritmos de aprendizado de máquina.

## Pré-processamento

Antes de treinar um modelo de aprendizado de máquina, é essencial realizar o pré-processamento dos dados, garantindo que eles estejam em um formato adequado para análise. O livro de Hastie, Tibshirani e Friedman (2009) destaca as principais etapas dessa fase:

- Normalização e Padronização: Ajusta a escala dos dados para que diferentes variáveis tenham contribuições equilibradas no modelo. Isso evita que atributos com valores muito grandes dominem a análise.
- Tratamento de Valores Ausentes: Implementação de estratégias para lidar com dados faltantes, como imputação (substituição por média, mediana ou valores mais prováveis) ou exclusão de registros incompletos.
- Codificação de Variáveis Categóricas: Conversão de variáveis categóricas em formatos numéricos que os algoritmos possam interpretar, como a técnica one-hot encoding.

Essas etapas garantem que os dados estejam em um formato adequado, melhorando a eficiência e a precisão do modelo.

## Overfeeting e underfeeting

Hastie, Tibshirani e Friedman (2009) também discutem dois desafios críticos no treinamento de modelos de aprendizado de máquina: o overfitting (sobreajuste) e o underfitting (subajuste).

- Overfitting (Sobreajuste): Ocorre quando o modelo se ajusta excessivamente aos dados de treinamento, capturando padrões específicos (e até ruídos) que não se generalizam bem para novos dados. Isso resulta em um alto desempenho no conjunto de treino, mas um fraco desempenho em dados desconhecidos. Técnicas como regularização, validação cruzada e aumento de dados podem ajudar a mitigar esse problema. 
- Underfitting (Subajuste): Acontece quando o modelo é excessivamente simples e não consegue capturar padrões relevantes nos dados. Isso pode ocorrer, por exemplo, quando se utiliza uma regressão linear para modelar uma relação complexa entre variáveis. Estratégias como o uso de modelos mais sofisticados, o ajuste de hiperparâmetros e a adição de mais características relevantes ao conjunto de treinamento podem ser aplicadas para evitar o subajuste.


---

# Algoritmos de aprendizado supervisionado

O aprendizado supervisionado é uma abordagem do aprendizado de máquina na qual um modelo é treinado a partir de um conjunto de dados rotulado, ou seja, cada entrada do treinamento possui um rótulo correspondente que representa sua classificação correta. Dessa forma, o modelo aprende a associar padrões nos dados às respostas esperadas, permitindo a realização de previsões em novas amostras.

## K-Nearest Neighbors

O algoritmo **k-nearest neighbors (KNN)** é um dos métodos mais simples e eficazes no aprendizado supervisionado. Ele funciona com base na similaridade entre os dados, classificando uma nova amostra com base nas **k** amostras mais próximas dentro do conjunto de treinamento. A proximidade entre os pontos é determinada por uma métrica de distância, sendo a **distância euclidiana** uma das mais utilizadas.

De acordo com **Chomboon et al. (2015)**, o KNN é um algoritmo semi-supervisionado que necessita de um conjunto de treinamento e de um valor predefinido de **k** para encontrar os **k vizinhos mais próximos** de um dado desconhecido. Caso os **k vizinhos** pertençam a classes diferentes, a classe da nova amostra será definida com base na **maioria** dos vizinhos.

Um exemplo prático pode ser observado na classificação do conjunto de dados **Iris**, em que um ponto de coordenadas **(5, 1.45)** precisa ser classificado. Considerando **k = 8**, com base na **distância euclidiana**, os oito vizinhos mais próximos são identificados, pertencendo a duas classes possíveis: **virginica** (com dois vizinhos) e **versicolor** (com seis vizinhos). Como a maioria dos pontos pertence à classe **versicolor**, o novo ponto é classificado dentro dessa categoria (**CHOMBOON et al., 2015**).

O KNN apresenta vantagens, como a simplicidade e a capacidade de lidar com problemas complexos sem a necessidade de um modelo matemático explícito. No entanto, ele pode ser computacionalmente custoso quando aplicado a grandes volumes de dados, já que a classificação exige o cálculo da distância para todas as amostras no conjunto de treinamento.

## Modelos Lineares  

Os **modelos lineares** são uma das abordagens mais clássicas no aprendizado supervisionado, sendo amplamente utilizados para tarefas de **classificação** e **regressão**. Eles assumem que a relação entre as variáveis independentes (inputs) e a variável dependente (output) pode ser representada por uma combinação linear dos atributos do conjunto de dados.  

Entre os modelos mais comuns, destacam-se:  

- **Regressão Linear**: Utilizada quando a variável de saída é contínua, esse modelo ajusta uma reta que melhor representa a relação entre as variáveis preditoras e a variável alvo.  
- **Regressão Logística**: Aplicada em problemas de classificação binária, a regressão logística calcula a probabilidade de um dado pertencer a uma determinada classe por meio da função sigmoide.  
- **Máquinas de Vetores de Suporte (SVM) Linear**: Em sua versão linear, a SVM encontra um **hiperplano ótimo** que separa os dados de diferentes classes com a maior margem possível.  

Esses métodos são eficientes em problemas onde a separação dos dados pode ser feita por uma reta ou um hiperplano, mas podem apresentar dificuldades quando a relação entre os dados for altamente não linear. Para lidar com essas limitações, técnicas como **transformação de características** e **uso de kernels** são frequentemente aplicadas para expandir a capacidade dos modelos lineares.  

## Classificadores Bayesianos  

Os **classificadores bayesianos** são baseados no **Teorema de Bayes**, que descreve a probabilidade de um evento ocorrer considerando informações prévias sobre esse evento. Esses algoritmos são amplamente utilizados em tarefas de **classificação probabilística**, pois oferecem um modelo robusto para lidar com dados ruidosos e de alta dimensionalidade.  

O principal classificador bayesiano é o **Naïve Bayes**, que assume que todas as características dos dados são **condicionalmente independentes**, o que simplifica os cálculos e torna o modelo extremamente rápido e eficiente, mesmo com grandes conjuntos de dados.  

A fórmula do **Teorema de Bayes** é dada por:  

$$P(C | X) = \frac{P(X | C) P(C)}{P(X)}$$

onde:  

- $( P(C | X) )$ é a probabilidade de uma amostra pertencer à classe $( C )$ dado o conjunto de características $( X )$;  
- $( P(X | C) )$ é a probabilidade de observar os atributos $( X )$ dado que a amostra pertence à classe $( C )$;  
- $( P(C) )$ é a probabilidade a priori da classe $( C )$;  
- $( P(X) )$ é a probabilidade total dos atributos $( X )$.  

Os classificadores bayesianos são amplamente utilizados em aplicações como **filtragem de spam**, **análise de sentimentos** e **reconhecimento de padrões**. Apesar de sua simplicidade, o Naïve Bayes pode obter resultados surpreendentemente bons em problemas de classificação, especialmente quando os dados seguem distribuições bem definidas.  

---
# Redes Neurais e aprendizado profundo

---

# ExplainableArtificial Intelligence (XAI)

---

# Algoritmos de aprendizado não supervisionado

## K-means Clustering
## Self-organized Maps


---

# Aprendizado por reforço

## Q-Learning









## Referências

- HASTIE, T.; TIBSHIRANI, R.; FRIEDMAN, J. The Elements of Statistical Learning: Data Mining, Inference, and Prediction. 2. ed. New York: Springer, 2009.
- CHOMBOON, Kittipong et al. Um estudo empírico de métricas de distância para o algoritmo k-vizinho mais próximo. In: Anais da 3ª Conferência Internacional sobre Engenharia de Aplicação Industrial. 2015. p. 4.
