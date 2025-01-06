# Representação Atômica vs Fatorada

# Representação Atômica vs Fatorada

A **representação atômica** e a **representação fatorada** são duas abordagens distintas para representar um ambiente em sistemas de inteligência artificial (IA), cada uma com implicações sobre a complexidade e a expressividade da estrutura de pensamento de um agente. A **principal diferença** entre elas é a **complexidade**: enquanto a representação atômica é mais simples e adequada para tarefas diretas, a representação fatorada adiciona mais detalhes, permitindo um planejamento mais preciso, porém com maior **custo computacional**. Schier (2024) observa que "quanto mais detalhado for o ambiente, mais complexa será a estrutura de representação". A escolha entre essas abordagens depende das exigências da tarefa e do equilíbrio entre simplicidade e detalhamento.

## 1. Representação Atômica
Na **representação atômica**, o ambiente é descrito de forma unitária, com estados simples e isolados, sem decomposição ou detalhamento adicional. Como Schier (2024) aponta, "o estado do ambiente de tarefas, obtido por meio dos sensores, também não pode ser decomposto em qualquer tipo de estrutura interna". Nesse modelo, a transição entre estados ocorre de forma direta, sem levar em consideração atributos ou características adicionais do ambiente. Um exemplo prático seria um agente que se desloca de um ponto A para um ponto B em linha reta, sem considerar obstáculos ou as condições do percurso. O agente apenas sabe que o ponto de partida é A e o destino é B, sem mais informações sobre o caminho ou o próprio agente.

## 2. Representação Fatorada
Na **representação fatorada**, o ambiente é descrito de forma mais detalhada, atribuindo atributos específicos aos objetos que o compõem. Esses atributos podem variar entre os estados, proporcionando uma descrição mais rica e expressiva. Como Schier (2024) explica, "os estados do ambiente podem ser caracterizados por meio da atribuição de um determinado número de atributos aos objetos". No exemplo do deslocamento, além de simplesmente mover-se de A para B, o agente agora pode considerar fatores como a qualidade do terreno, a quantidade de combustível disponível ou até o tempo estimado para a viagem, permitindo um planejamento mais refinado e adaptativo.

Apesar das diferenças de complexidade, Schier (2024) conclui que "independentemente do grau de expressividade do ambiente, um agente racional de IA conseguiria se deslocar de A para B utilizando qualquer uma das três formas de representações". Isso demonstra a flexibilidade dos modelos de representação em IA, que podem ser ajustados conforme a necessidade de precisão e detalhamento em diferentes contextos.

# Definindo Problemas de satisfação de condições
# Tipos de condições
# Consistência
## 1. Nó
## 2. Arco
## 3. Trajeto
## 4. K
## 5. Globais
# Algoritmos
# Estrutura de problemas


### Referencias

SCHIER, Ubirajara Theodoro. O RACIOCÍNIO PRÁTICO E INTELIGÊNCIA ARTIFICIAL: A NECESSIDADE DE EVOLUÇÃO DE UMA ESTRUTURA DE PENSAMENTO HIERÁRQUICA PARA UM ESTRUTURA DE PENSAMENTO EM REDE. Polymatheia-Revista de Filosofia, v. 17, n. 1, p. 360-385, 2024.

Russell, S. and Norvig, P., Artificial Intelligence - A Modern Approach, 4th ed, Pearson, 2022
