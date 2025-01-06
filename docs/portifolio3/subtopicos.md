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

Por exemplo, no problema de coloração de mapas, o objetivo é colorir cada região com uma cor (vermelho, verde ou azul) de forma que regiões vizinhas tenham cores diferentes. Esse tipo de modelagem é eficiente porque permite descartar atribuições inválidas rapidamente e focar em soluções viáveis.

Os PSRs são amplamente aplicados devido à sua flexibilidade e eficiência na resolução de problemas complexos, especialmente quando comparados com métodos tradicionais de busca em espaço de estados.

---

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
