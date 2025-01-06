# Representação Atômica vs Fatorada

A **representação atômica** e a **representação fatorada** são duas abordagens distintas para representar estados em ambientes de sistemas de inteligência artificial (IA). Enquanto a representação atômica trata os estados como entidades indivisíveis e simples, a representação fatorada decompõe esses estados em variáveis e atributos, permitindo maior flexibilidade e expressividade. Ambas as abordagens possuem vantagens e limitações, dependendo do tipo de problema a ser resolvido e dos requisitos de detalhamento e eficiência computacional.

## 1. Representação Atômica

Na **representação atômica**, os estados do ambiente são tratados como **indivisíveis** ou **caixas-pretas**, sem qualquer estrutura interna que possa ser manipulada diretamente. Russell e Norvig (2022) destacam que, "do ponto de vista do algoritmo de busca, cada estado é atômico, ou indivisível — uma caixa-preta, sem estrutura interna". Isso implica que as transições entre os estados são definidas de forma direta, sem levar em consideração características ou atributos internos. 

Como exemplo, podemos imaginar um agente que deve se deslocar de um ponto A para um ponto B. Na abordagem atômica, o agente sabe apenas que deve ir de A para B, sem considerar elementos adicionais, como o tipo de terreno ou o tempo necessário. Essa simplicidade reduz a complexidade computacional, mas limita a capacidade do agente de realizar planejamentos mais elaborados. Schier (2024) reforça que "o estado do ambiente de tarefas, obtido por meio dos sensores, também não pode ser decomposto em qualquer tipo de estrutura interna".

## 2. Representação Fatorada

A **representação fatorada**, por outro lado, permite descrever os estados do ambiente como conjuntos de **variáveis**, cada uma com um valor associado. Segundo Russell e Norvig (2022), "utilizaremos uma representação fatorada para cada estado: um conjunto de variáveis, cada qual com um valor". Isso possibilita uma descrição mais detalhada e rica do ambiente, onde os estados podem ser caracterizados por atributos específicos que variam conforme a situação.

Por exemplo, ao se deslocar de A para B, um agente que utiliza uma representação fatorada pode considerar variáveis como a qualidade do terreno, a distância, o consumo de energia e o tempo estimado. Essa abordagem é particularmente útil em problemas de satisfação de restrição (PSR), nos quais o objetivo é atribuir valores às variáveis de forma a satisfazer todas as restrições impostas.

Schier (2024) complementa que "os estados do ambiente podem ser caracterizados por meio da atribuição de um determinado número de atributos aos objetos". Isso oferece ao agente uma base mais detalhada para tomar decisões e planejar ações, mas com um custo computacional mais elevado em comparação à abordagem atômica.

---

# Definindo Problemas de satisfação de condições

Um **Problema de Satisfação de Restrições (PSR)** é uma forma de modelar problemas em termos de variáveis, valores e restrições. Ele é definido por três componentes principais:

- **Variáveis (X)**: Representam os elementos do problema, como X₁, X₂, ..., Xₙ.  
- **Domínios (D)**: Conjuntos de valores possíveis para cada variável, como D₁, D₂, ..., Dₙ.  
- **Restrições (C)**: Regras que especificam combinações válidas de valores entre as variáveis.  

Uma **solução** para um PSR é uma atribuição de valores que seja consistente (não viole nenhuma restrição) e completa (todas as variáveis têm um valor). 

![image](https://github.com/user-attachments/assets/ff5b948e-744a-46b7-81f7-d3150b482dd2)


Por exemplo, no problema de coloração de mapas, o objetivo é colorir cada região com uma cor (vermelho, verde ou azul) de forma que regiões vizinhas tenham cores diferentes. Esse tipo de modelagem é eficiente porque permite descartar atribuições inválidas rapidamente e focar em soluções viáveis.

Os PSRs são amplamente aplicados devido à sua flexibilidade e eficiência na resolução de problemas complexos, especialmente quando comparados com métodos tradicionais de busca em espaço de estados.

---

# Tipos de condições

- **Restrições Unitárias**: Limitam o valor de uma única variável. Por exemplo, uma região do mapa não pode ser verde (e.g., SA ≠ G).

- **Restrições Binárias**: Estabelecem relações entre duas variáveis. Por exemplo, duas regiões adjacentes não podem ter a mesma cor (e.g., SA ≠ NSW).

- **Restrições Ternárias**: Relacionam três variáveis, como em uma condição de ordem (e.g., X > Y > Z).

- **Restrições Globais**: Envolvem um número arbitrário de variáveis, mas não necessariamente todas. Um exemplo comum é a restrição "TodosDiferentes" (e.g., Alldiff(A1, A2, A3, B1, B2, B3, C1, C2, C3)).

Qualquer PSR pode ser transformado em um PSR que contenha apenas restrições binárias. Por exemplo, uma restrição ternária como X > Y > Z pode ser reescrita como X > Y e Y > Z.

## Condições de Preferência

Além das restrições necessárias, podem-se incluir condições de preferência para modelar soluções ideais. Por exemplo:

- Nenhum professor pode dar duas aulas ao mesmo tempo (condição necessária).  
- O professor A prefere dar aulas pela manhã (condição preferencial).  
- Uma sala X deve, preferencialmente, receber turmas maiores.

As condições de preferência são úteis para encontrar soluções que, embora válidas, sejam também otimizadas para os critérios desejados.

---
# Consistência

A consistência local é uma técnica central em algoritmos para PSRs que busca simplificar o problema antes ou durante a busca de soluções. Essa abordagem utiliza as restrições do problema para reduzir os valores possíveis de variáveis, eliminando valores inconsistentes e propagando essas reduções para outras variáveis. Visualizando o problema como um grafo, onde as variáveis são nós e as restrições binárias são arcos, a consistência local pode ser aplicada em diferentes níveis, como consistência de nó, arco, caminho e consistência k. Além disso, restrições globais podem ser usadas para simplificar problemas complexos de maneira eficiente.

## 1. Nó

A *consistência de nó* é um conceito aplicado a redes de restrições (PSR - *Constraint Satisfaction Problems*), onde uma variável é considerada *nó-consistente* se todos os valores no seu domínio satisfizerem as restrições unárias dessa variável. Em outras palavras, cada valor permitido para uma variável deve cumprir com as condições impostas a essa variável.

Por exemplo, no problema de coloração do mapa da Austrália (Russell & Norvig, 2022), onde a região "SA" não pode ser colorida de verde, se o domínio inicial de "SA" for {vermelho, verde, azul}, podemos tornar essa variável nó-consistente ao eliminar a cor verde. O domínio reduzido de "SA" seria então {vermelho, azul}.

A rede é considerada *nó-consistente* se todas as suas variáveis forem nó-consistentes. Em um PSR, é possível eliminar as restrições unárias de todas as variáveis ao executar a consistência de nó.

Essa abordagem também é útil para transformar restrições n-árias em binárias, o que facilita a resolução de PSRs, pois muitos solucionadores de PSR trabalham com restrições binárias (Russell & Norvig, 2022).

## 2. Arco
## 3. Trajeto
## 4. K
## 5. Globais
# Algoritmos
# Estrutura de problemas


### Referencias

SCHIER, Ubirajara Theodoro. O RACIOCÍNIO PRÁTICO E INTELIGÊNCIA ARTIFICIAL: A NECESSIDADE DE EVOLUÇÃO DE UMA ESTRUTURA DE PENSAMENTO HIERÁRQUICA PARA UM ESTRUTURA DE PENSAMENTO EM REDE. Polymatheia-Revista de Filosofia, v. 17, n. 1, p. 360-385, 2024.

Russell, S. and Norvig, P., Artificial Intelligence - A Modern Approach, 4th ed, Pearson, 2022
