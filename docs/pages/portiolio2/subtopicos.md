## 1. Agentes de solução de problemas
  ### 1.1 Objetivos
  Agentes inteligentes buscam maximizar seu desempenho, o que é alcançado ao definir objetivos claros e específicos. Esses objetivos ajudam a simplificar a tomada de decisão, permitindo que o agente filtre as ações mais relevantes para alcançar o resultado desejado. Por exemplo, em uma viagem de férias saindo de Goiânia, o agente pode definir como objetivo chegar a Brasília. Com esse objetivo em mente, o agente pode focar apenas nas rotas que levam à capital federal, tornando a escolha da estrada mais eficiente.

  ### 1.2 Formulação de problemas
  Para alcançar seus objetivos, o agente precisa formular o problema de maneira eficaz, selecionando as ações e estados mais adequados para a solução. No exemplo da viagem de Goiânia a Brasília, o objetivo é chegar a Brasília, e o agente deve considerar ações de direção entre as cidades. Isso significa que ele pode avaliar rotas como ir de Goiânia para Formosa, ou de Alexânia para o Distrito Federal. A formulação do problema envolve decidir que tipo de ações e estados são relevantes para alcançar o objetivo de forma eficiente, ignorando outros detalhes irrelevantes.

  ### 1.3 Busca e execução

  A resolução de problemas por um agente envolve um processo de busca para encontrar uma sequência de ações que o conduza ao seu objetivo. No exemplo de uma viagem de Goiânia a Brasília, o agente precisa buscar a melhor rota que o leve até a capital federal. Após identificar essa sequência de ações, o agente a executa sem fazer ajustes baseados em percepções durante o percurso. Isso caracteriza um sistema de malha aberta, em que o agente segue rigidamente o plano, sem reagir a mudanças no ambiente ao longo da execução.

  ### 1.4 Definindo problemas
  A formulação de um problema pode ser descrita por cinco componentes principais: o estado inicial, as ações disponíveis, o modelo de transição, o teste de objetivo e a função de custo. Para a viagem de Goiânia a Brasília, o estado inicial seria a posição do agente em Goiânia. As ações possíveis são as rotas entre as cidades, como Goiânia para Formosa ou Goiânia para Alexânia. O modelo de transição descreve como cada ação leva a um novo estado. O teste de objetivo é atingir Brasília, e a função de custo pode ser definida pelo tempo ou distância das rotas. Usando essas informações, o agente pode encontrar a solução ótima.
  
## 2. Problemas de malha aberta e de malha fechada
## 3. Algoritmos de busca
  Os algoritmos de busca são fundamentais para a resolução de problemas em inteligência artificial, pois permitem que um agente encontre uma sequência de ações que o leve ao seu objetivo. Esses algoritmos são projetados para explorar um espaço de estados, que é o conjunto de todas as possíveis situações que o agente pode encontrar durante sua tarefa.
  ### 3.1 Busca cega
  Busca cega, também conhecida como busca não-informada, é uma estratégia de resolução de problemas que não utiliza conhecimento prévio sobre o ambiente ou o objetivo final. Essas técnicas exploram o espaço de estados de forma sistemática, baseando-se apenas em uma função de enfileiramento para determinar os próximos passos.
    #### 3.1.1 Busca em largura
      Explora todos os estados em um nível antes de avançar para o próximo. É útil para encontrar a solução mais curta, mas consome mais memória.
      ![Busca em largura](../assets/buscaEmLargura.png)
      Figura 1: Nesta figura temos uma demonstração teórica de como funciona a busca em largura.
      
  ### 3.2 Busca informada
## 4. Funções Heurísticas
## 5. Busca em ambientes complexos
## 6. Algoritmos genéticos

referencias:

Russell, S. and Norvig, P., Artificial Intelligence - A Modern Approach, 4th ed,
Pearson, 2022
[https://www.scielo.br/j/ea/a/c4sqqrthGMS3ngdBhGWtKhh/?format=html](https://doi.org/10.1590/s0103-4014.2021.35101.004)

Silva, D. M., Freitas, V. M., FERNANDES JR, J. R., Uchôa, J. Q., & Schneider, B. de O. (2004). Implementação de uma Biblioteca para Busca Informada e Não-Informada em Espaço de Estados. INFOCOMP Journal of Computer Science, 3(1), 48–61. Retrieved from https://infocomp.dcc.ufla.br/index.php/infocomp/article/view/63
