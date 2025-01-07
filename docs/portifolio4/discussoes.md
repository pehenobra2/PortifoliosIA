# Algoritmo de Resolução

O **algoritmo de resolução** é uma técnica fundamental utilizada para a inferência em lógica proposicional e lógica de predicados, permitindo deduzir novas informações a partir de uma base de conhecimento. Muito utilizado em inteligência artificial, especialmente em sistemas de prova automática e agentes baseados em lógica, a resolução é um método essencial para lidar com problemas complexos de forma eficaz.

## Princípio da Resolução

A resolução consiste em combinar duas cláusulas que contêm literais complementares, resultando em uma nova cláusula que não possui os literais opostos. O objetivo desse processo é simplificar as cláusulas, reduzindo o problema a uma forma mais simples, até que se alcance uma contraditoriedade ou uma cláusula que contenha a informação desejada.

### Etapas da Resolução

1. **Seleção das cláusulas:** O processo de resolução começa com a escolha de duas cláusulas que possuam literais complementares. Por exemplo, se uma cláusula contém `A` e outra contém `¬A`, estes literais são complementares.
   
2. **Resolução dos literais:** Após identificar os literais complementares, eles são eliminados, e o restante das cláusulas é combinado em uma nova cláusula. A resolução, portanto, é a operação que remove os literais opostos e funde os literais restantes. 

3. **Repetição do processo:** A resolução continua até que não seja mais possível resolver novas cláusulas ou até que se chegue a uma contraditoriedade (ou uma cláusula vazia), indicando que a sentença é válida.

### Exemplo de Resolução

Considere as seguintes cláusulas:

- **Cláusula 1:** ( A ∨ B )
- **Cláusula 2:** ( ¬A ∨ C )

A resolução é realizada da seguinte maneira:

1. Identificam-se os literais complementares: \( A \) e \( \neg A \).
2. Os literais complementares são removidos e os literais restantes são unidos: \( B \vee C \).

A cláusula resultante da resolução entre \( A \vee B \) e \( \neg A \vee C \) é:

- **Cláusula resolvida:** \( B \vee C \)

### Aplicação da Resolução em Provas

A resolução pode ser aplicada para provar que uma sentença é uma consequência lógica de uma base de conhecimento. Para isso, utiliza-se o princípio da **prova por refutação**:

1. Se a base de conhecimento é consistente com a sentença que se deseja provar, a resolução não gerará contraditoriedade.
2. Se a base de conhecimento e a negação da sentença levam a uma contraditoriedade, isso significa que a sentença original é uma consequência lógica.

### Complexidade da Resolução

Embora o algoritmo de resolução seja **completo** (sempre encontra uma solução, caso ela exista), sua **complexidade computacional** pode ser alta, especialmente em problemas de grande escala. Isso se deve à **explosão combinatória**: o número de resoluções pode crescer exponencialmente à medida que o tamanho da base de conhecimento aumenta.

### Aplicações da Resolução

A resolução encontra várias aplicações práticas em inteligência artificial, incluindo:

- **Sistemas de Prova Automática:** Automatizam a demonstração de teoremas em lógica formal, usando a resolução para derivar conclusões.
- **Sistemas de Diagnóstico:** Utilizada para identificar falhas em sistemas complexos, deduzindo possíveis falhas a partir de hipóteses e observações.
- **Agentes Baseados em Lógica:** Em ambientes como o **Wumpus World**, agentes utilizam a resolução para inferir informações sobre o ambiente e tomar decisões baseadas nas percepções adquiridas.

## Considerações Finais

O algoritmo de resolução é uma ferramenta poderosa e amplamente utilizada para inferir novas informações a partir de uma base de conhecimento. Apesar de sua alta complexidade computacional, sua completude e capacidade de ser aplicado em diversas áreas da inteligência artificial tornam-no essencial em sistemas de raciocínio lógico e em agentes autônomos.
