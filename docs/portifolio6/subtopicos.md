# APRENDIZADO DE MÁQUINA

O Aprendizado de Máquina (Machine Learning) é um campo da Inteligência Artificial (IA) que se dedica ao desenvolvimento de sistemas capazes de aprender a partir de dados e aprimorar seu desempenho ao longo do tempo, sem a necessidade de programação explícita para cada situação. Em vez de depender de um conjunto fixo de regras predefinidas, os modelos de aprendizado de máquina identificam padrões, fazem previsões e ajustam seus resultados à medida que recebem novos dados, tornando-se mais precisos e eficientes.

Essa abordagem revolucionou diversas áreas, possibilitando que computadores realizem tarefas complexas que antes requeriam intervenção humana. Entre suas aplicações mais comuns, destacam-se o reconhecimento de voz e imagem, sistemas de recomendação personalizados (como os utilizados por plataformas de streaming e e-commerce), detecção de fraudes em transações financeiras e até a condução autônoma de veículos.

O avanço dessa tecnologia tem sido impulsionado pelo crescimento exponencial da capacidade computacional, pelo acesso a grandes volumes de dados e pelo desenvolvimento de algoritmos cada vez mais sofisticados. Com isso, o aprendizado de máquina se tornou uma ferramenta indispensável para a automação de processos, a extração de insights estratégicos e a criação de soluções inovadoras em diversos setores da indústria e da ciência.

# TIPOS DE APRENDIZADO DE MÁQUINA

O Aprendizado de Máquina pode ser classificado em três principais categorias, dependendo da forma como os dados são utilizados para treinar os modelos: aprendizado supervisionado, aprendizado não supervisionado e aprendizado por reforço. Cada uma dessas categorias possui características específicas e é aplicada a diferentes problemas.

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

As Redes Neurais (RNs) são sistemas computacionais inspirados no funcionamento do cérebro humano, desenvolvidos para executar tarefas cognitivas como reconhecimento de padrões, percepção e controle motor. Esses modelos são baseados nos neurônios biológicos, que estão organizados de maneira eficiente para processar informações de forma paralela e não linear. Segundo Haykin (2001), o cérebro humano organiza seus neurônios de maneira que permite a execução de tarefas complexas de forma mais rápida e eficiente do que sistemas computacionais tradicionais. As RNs buscam emular essa estrutura, utilizando componentes eletrônicos ou programas de computador para realizar funções semelhantes às do cérebro (NETO, 2015).

O funcionamento de uma RNA baseia-se em unidades de processamento chamadas neurônios artificiais, que imitam os neurônios biológicos. Cada neurônio artificial recebe entradas, atribui pesos sinápticos, possui um somador (bias) e aplica uma função de ativação. As entradas são multiplicadas pelos pesos sinápticos, e a soma resultante é passada pela função de ativação, que limita a amplitude da saída do neurônio. Essa estrutura permite que as RNAs se ajustem durante o treinamento, aplicando aprendizado supervisionado ou não supervisionado e otimizando os pesos sinápticos para melhorar a precisão das previsões (HAYKIN, 2001; BIANCHINI, 2004).

O Deep Learning (Aprendizado Profundo) emergiu como uma extensão das redes neurais, abordando desafios relacionados ao processamento de grandes volumes de dados com alta dimensionalidade. Essa técnica se destaca em tarefas como o reconhecimento de imagens, áudio e texto, sendo amplamente aplicada em grandes empresas como Google, Microsoft e Baidu, que a utilizam em inovações como carros autônomos, motores de busca aprimorados e reconhecimento visual (JOST, 2015).

Uma das características essenciais do Deep Learning é a sua capacidade de aprender representações hierárquicas de dados. Bengio (2009) descreve que redes profundas são formadas por várias camadas, onde cada camada aprende representações mais abstratas e complexas dos dados em comparação com a camada anterior. Essa estrutura permite que redes profundas detectem padrões e características de alto nível, representando um avanço significativo em relação às abordagens anteriores de aprendizado supervisionado, que se concentravam em aprender uma única função com um conjunto de parâmetros.

A principal diferença entre Deep Learning e Machine Learning (Aprendizado de Máquina) está no tipo de função que cada uma aprende. Técnicas tradicionais de aprendizado de máquina são frequentemente chamadas de “rasas” (shallow) e buscam aprender uma função simples que transforma os dados de entrada em um resultado. Por outro lado, o Deep Learning utiliza várias camadas para compor funções complexas, permitindo uma transformação gradual e cada vez mais refinada dos dados, o que é especialmente útil para lidar com grandes volumes de dados não estruturados (PONTI; COSTA, 2017).

Em resumo, tanto as redes neurais quanto o aprendizado profundo representam avanços significativos nas técnicas de aprendizado de máquina. Ao simular o comportamento dos neurônios biológicos e aplicar múltiplas camadas de processamento, essas abordagens têm se mostrado fundamentais em uma ampla gama de aplicações, como reconhecimento de voz, imagens e até na condução autônoma de veículos.

---

# Explainable Artificial Intelligence (XAI)

A Explainable Artificial Intelligence (XAI) é um conceito fundamental no desenvolvimento de modelos de IA, pois visa permitir que os usuários compreendam e confiem nas decisões feitas por algoritmos de aprendizado de máquina. A XAI é crucial para mitigar os problemas associados aos chamados modelos de "caixa preta", que, muitas vezes, são difíceis de interpretar, mesmo pelos próprios criadores dos algoritmos. Além de garantir maior transparência e confiabilidade, a XAI também facilita a conformidade com regulamentos e assegura que decisões automatizadas possam ser auditadas e ajustadas, quando necessário (IBM, 2025).

---

# Algoritmos de aprendizado não supervisionado

## K-means Clustering
O algoritmo K-means é uma técnica popular de aprendizado não supervisionado que busca agrupar dados em clusters com base na proximidade dos pontos em relação aos centroides. Ele utiliza a distância euclidiana para determinar a similaridade entre os pontos e seus centroides, dividindo-os em grupos distintos. A inicialização dos centroides é crítica e pode ser otimizada com técnicas como o k-means++. O objetivo do algoritmo é minimizar a inércia, que mede a compactação dos clusters, e é avaliado por métricas como o índice de Dunn, que compara a distância entre clusters distintos (IBM, 2025).

## Self-organized Maps

Os Self-Organized Maps (SOM), ou Mapas Auto-Organizáveis, são uma técnica de aprendizado não supervisionado baseada na rede neural que visa mapear dados de alta dimensionalidade em uma grade de unidades de menor dimensionalidade. Os SOMs são particularmente úteis para visualizar dados complexos, agrupando pontos de dados semelhantes em regiões próximas da rede. A principal característica desse algoritmo é a sua capacidade de preservar as relações topológicas dos dados, ou seja, pontos de dados similares ficam próximos no mapa, facilitando a análise e a interpretação dos resultados. Além disso, SOMs são frequentemente usados em áreas como reconhecimento de padrões, visualização de dados e análise exploratória de dados.

---

# Aprendizado por reforço

## Q-Learning

O Q-Learning é um algoritmo de aprendizado por reforço que busca aprender a política ótima de um agente em um ambiente. Através de interações com o ambiente, o algoritmo atualiza uma tabela de Q-valores que representam a recompensa esperada para cada ação tomada em um estado específico. A atualização dos valores é realizada utilizando a equação de Bellman, que ajusta os Q-valores com base na recompensa imediata e nas recompensas futuras esperadas. Isso permite que o agente tome decisões mais informadas e aprenda a maximizar a recompensa ao longo do tempo.

---


## REFERÊNCIAS

- HASTIE, T.; TIBSHIRANI, R.; FRIEDMAN, J. *The Elements of Statistical Learning: Data Mining, Inference, and Prediction*. 2. ed. New York: Springer, 2009.
- CHOMBOON, Kittipong et al. Um estudo empírico de métricas de distância para o algoritmo k-vizinho mais próximo. In: Anais da 3ª Conferência Internacional sobre Engenharia de Aplicação Industrial. 2015. p. 4.
- BENGIO, Yoshua. Learning Deep Architectures for AI. *Foundations and Trends in Machine Learning*, v. 2, n. 1, p. 1–127, 2009.
- BIANCHINI, João. *Redes Neurais Artificiais: O modelo de neurônio biológico e suas aplicações*. 2004.
- HAYKIN, Simon. *Neural Networks: A Comprehensive Foundation*. 2. ed. Upper Saddle River: Prentice Hall, 2001.
- JOST, Michael. *Deep Learning and Applications: A New Era of Intelligent Systems*. 2015.
- NETO, José de Almeida. *Redes Neurais: Princípios e Aplicações*. 2015.
- PONTI, Marco; COSTA, Antonio. *Deep Learning: A Powerful Tool for Artificial Intelligence*. Springer, 2017.
- YANG, Xin. *Non-Supervised Learning: Challenges and Approaches*. Springer, 2013.
- IBM. O que é IA explicável (XAI)? IBM, 2025. Disponível em: <https://www.ibm.com/br-pt/topics/explainable-ai>. Acesso em: 18 fev. 2025.
- IBM. O que é o agrupamento K-means? Disponível em: <https://www.ibm.com/br-pt/topics/k-means-clustering>. Acesso em: 18 fev. 2025.
