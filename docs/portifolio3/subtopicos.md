# Representação Atômica vs Fatorada

A **representação atômica** e a **representação fatorada** são duas abordagens distintas para representar estados em ambientes de sistemas de inteligência artificial (IA). A representação atômica trata os estados como **indivisíveis**, enquanto a representação fatorada decompõe os estados em variáveis e atributos, oferecendo maior flexibilidade e expressividade. Ambas as abordagens possuem vantagens e limitações, dependendo do problema e dos requisitos de detalhamento e eficiência computacional.

## 1. Representação Atômica

Na **representação atômica**, os estados são tratados como **caixas-pretas**, sem estrutura interna manipulável. Russell e Norvig (2022) destacam que, "do ponto de vista do algoritmo de busca, cada estado é atômico — uma caixa-preta, sem estrutura interna". As transições entre os estados são definidas de forma direta, sem considerar características ou atributos internos.

Por exemplo, em um agente que deve se deslocar de um ponto A para um ponto B, a abordagem atômica ignora detalhes como tipo de terreno ou tempo necessário, focando apenas na transição entre A e B. Embora simples e de baixo custo computacional, essa abordagem limita a capacidade do agente de realizar planejamentos mais elaborados. Schier (2024) reforça que "o estado do ambiente de tarefas não pode ser decomposto em qualquer tipo de estrutura interna".

## 2. Representação Fatorada

A **representação fatorada** descreve os estados como conjuntos de **variáveis**, cada uma com um valor associado. Segundo Russell e Norvig (2022), "utilizamos uma representação fatorada para cada estado: um conjunto de variáveis, cada qual com um valor". Essa abordagem oferece uma descrição mais detalhada e rica do ambiente, permitindo que o estado seja caracterizado por atributos específicos.

Por exemplo, ao se deslocar de A para B, um agente com representação fatorada pode considerar variáveis como qualidade do terreno, distância, consumo de energia e tempo estimado. Essa abordagem é útil especialmente em problemas de satisfação de restrições (PSR), onde o objetivo é atribuir valores às variáveis de forma a satisfazer as restrições impostas.

Schier (2024) complementa que "os estados do ambiente podem ser caracterizados através da atribuição de atributos aos objetos". Isso dá ao agente mais informações para tomar decisões, mas implica maior custo computacional em comparação com a abordagem atômica.

---

# Definindo Problemas de Satisfação de Restrições (PSR)

Um **Problema de Satisfação de Restrições (PSR)** modela problemas em termos de variáveis, valores e restrições. Ele é composto por três elementos principais:

- **Variáveis (X)**: Representam os elementos do problema (X₁, X₂, ..., Xₙ).
- **Domínios (D)**: Conjuntos de valores possíveis para cada variável (D₁, D₂, ..., Dₙ).
- **Restrições (C)**: Regras que especificam combinações válidas de valores entre as variáveis.

Uma **solução** para um PSR é uma atribuição de valores que seja **consistente** (não viole restrições) e **completa** (todas as variáveis têm um valor).

![Demonstração do problema de coloração de mapas](../assets/exemploMapas.png)  
*Figura 1: Demonstração do problema de coloração de mapas.*

Por exemplo, no problema de coloração de mapas, o objetivo é colorir as regiões de um mapa de modo que regiões vizinhas tenham cores diferentes. Este modelo é eficiente, pois permite eliminar rapidamente atribuições inválidas, concentrando-se nas soluções viáveis.

PSRs são amplamente aplicados devido à sua flexibilidade e eficiência na resolução de problemas complexos, especialmente quando comparados com métodos tradicionais de busca em espaço de estados.

---

# Tipos de Condições

- **Restrições Unitárias**: Limitam o valor de uma única variável (ex: SA ≠ G).
- **Restrições Binárias**: Estabelecem relações entre duas variáveis (ex: SA ≠ NSW).
- **Restrições Ternárias**: Relacionam três variáveis (ex: X > Y > Z).
- **Restrições Globais**: Envolvem várias variáveis, mas não necessariamente todas (ex: "TodosDiferentes").

Qualquer PSR pode ser transformado em um PSR com apenas restrições binárias, como no exemplo de uma restrição ternária X > Y > Z, que pode ser reescrita como X > Y e Y > Z.

## Condições de Preferência

Além das restrições necessárias, podem ser incluídas condições de preferência para modelar soluções ideais:

- Nenhum professor pode dar duas aulas ao mesmo tempo (condição necessária).  
- O professor A prefere dar aulas pela manhã (condição preferencial).  
- Uma sala X deve, preferencialmente, receber turmas maiores.

As condições de preferência ajudam a otimizar soluções válidas, alinhando-as aos critérios desejados.

---

# Consistência

A **consistência local** é uma técnica central para simplificar o problema antes ou durante a busca de soluções. Ela utiliza as restrições do problema para reduzir os valores possíveis de variáveis, eliminando valores inconsistentes e propagando essas reduções para outras variáveis. Visualizando o problema como um grafo, onde as variáveis são nós e as restrições binárias são arcos, a consistência local pode ser aplicada em diferentes níveis, como consistência de nó, arco, caminho e k-consistência.

## 1. Nó

A **consistência de nó** aplica-se quando uma variável é considerada *nó-consistente* se todos os valores no seu domínio satisfizerem as restrições unárias dessa variável. Por exemplo, no problema de coloração do mapa da Austrália, a região "SA" não pode ser verde. Se o domínio inicial de "SA" for {vermelho, verde, azul}, ao aplicar a consistência de nó, o domínio de "SA" se reduz a {vermelho, azul}.

Uma rede é considerada *nó-consistente* se todas as variáveis o forem, e a consistência de nó também pode transformar restrições n-árias em binárias, o que facilita a resolução de PSRs.

## 2. Arco

A **consistência de arco** ocorre quando todos os valores no domínio de uma variável satisfazem as restrições binárias relacionadas a essa variável. Uma rede é *arco-consistente* se todas as suas variáveis forem arco-consistentes. No exemplo de duas variáveis \(X\) e \(Y\) com a restrição \(Y = X^2\), a consistência de arco reduz os domínios das variáveis para garantir que a restrição seja respeitada.

Porém, a consistência de arco não impacta sempre as variáveis. No problema de coloração do mapa da Austrália, uma restrição de desigualdade entre duas regiões não afeta os domínios das variáveis.

## 3. Trajeto

A **consistência de trajeto** é uma forma mais forte de consistência, onde um conjunto de duas variáveis \(\{X_i, X_j\}\) é consistente com uma terceira variável \(X_m\) se, para cada atribuição consistente entre \(X_i\) e \(X_j\), existir uma atribuição para \(X_m\) que satisfaça as restrições binárias entre todas as variáveis. Esse conceito ajuda a verificar relações implícitas entre variáveis.

## 4. K

A **k-consistência** é uma propagação mais geral de consistência. Uma PSR é **k-consistente** se, para qualquer conjunto de \(k - 1\) variáveis e qualquer atribuição consistente, sempre é possível atribuir um valor consistente à \(k\)-ésima variável. Uma PSR é chamada de **fortemente k-consistente** se for k-consistente, \((k - 1)\)-consistente e assim sucessivamente.

PSRs fortemente n-consistentes podem ser resolvidos de maneira eficiente, mas a verificação de consistência é exponencial no pior caso e exige alto custo computacional.

## 5. Globais

As **restrições globais** envolvem múltiplas variáveis e podem ser tratadas com algoritmos especializados. Exemplos incluem a restrição *TodosDiferentes*, que exige valores distintos para todas as variáveis. A detecção de inconsistência pode ser feita, por exemplo, verificando o número de variáveis em relação ao número de valores possíveis.

---

# Algoritmos

A resolução de Problemas de Satisfação de Restrições (PSR) envolve a aplicação de algoritmos que ajudam a explorar e restringir os domínios das variáveis até que uma solução válida seja encontrada. Existem várias abordagens e técnicas para lidar com esses problemas, dependendo das características do problema específico e da eficiência desejada. Os algoritmos a seguir são comumente usados na resolução de PSRs, abordando desde a consistência das variáveis até métodos de busca e otimização. A escolha do algoritmo adequado pode impactar significativamente a performance na busca pela solução, e cada técnica possui suas vantagens em diferentes contextos de aplicação.

## 1. AC-3 (Algoritmo de Consistência de Arco)

O AC-3 é um algoritmo utilizado para garantir a consistência de arco em redes de restrições. Ele verifica todas as restrições binárias entre as variáveis, removendo valores incompatíveis nos domínios. O algoritmo continua até que não haja mais mudanças nos domínios, simplificando a resolução do problema.

## 2. Sudoku - Exemplo de CSP

O Sudoku é um exemplo clássico de PSR. As variáveis são as células do tabuleiro, os domínios são os números de 1 a 9, e as restrições garantem que cada número apareça uma vez por linha, coluna e bloco. Resolver o Sudoku envolve atribuir números às células de forma a satisfazer todas as restrições.

## 3. Pesquisa Backtracking para CSPs

A pesquisa backtracking é uma técnica de busca que tenta atribuir valores às variáveis de um CSP. Se uma atribuição viola uma restrição, o algoritmo retrocede e tenta outra possibilidade até encontrar uma solução ou determinar que o problema é impossível.

## 4. Intercalando Pesquisa e Inferência para CSPs

Essa abordagem combina pesquisa backtracking com técnicas de inferência, como AC-3 ou consistência de caminho, para reduzir os domínios das variáveis e simplificar a busca.

## 5. Busca Local para CSPs

A busca local envolve explorar soluções próximas a uma solução parcial já existente. Técnicas como *hill climbing* ou *simulated annealing* são usadas para melhorar soluções sem examinar todo o espaço de soluções, embora não garantam a solução global ótima.

---

# Estrutura de Problemas

A estrutura de um problema, representada pelo grafo de restrições, é fundamental para otimizar a busca por soluções em PSRs. Quando o problema pode ser decomposto em subproblemas independentes, como no caso da Tasmânia no mapa da Austrália, a solução se torna mais eficiente. Cada subproblema pode ser tratado separadamente, reduzindo a complexidade do problema global.

Uma estrutura eficiente é o grafo em árvore, onde as variáveis são conectadas por um único caminho, permitindo uma resolução linear do problema. A **Consistência Orientada de Arco (COA)** é aplicada para garantir que cada variável seja arco-consistente com as variáveis seguintes em uma ordenação.

Com a estruturação do PSR como uma árvore, o processamento das variáveis em ordem permite uma solução eficiente, mesmo com um número elevado de variáveis. A decomposição do problema em subproblemas e a aplicação da COA resultam em uma solução otimizada, com tempo linear, tornando a resolução de problemas complexos mais viável.
