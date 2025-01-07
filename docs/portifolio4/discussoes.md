# Algoritmo de Resolução

O **algoritmo de resolução** é uma técnica fundamental utilizada para inferência em lógica proposicional e lógica de predicados. Ele permite deduzir novas informações a partir de uma base de conhecimento e é amplamente utilizado em inteligência artificial, especialmente em sistemas de prova automática e agentes baseados em lógica.

## Princípio da Resolução

A resolução combina duas cláusulas com literais complementares, gerando uma nova cláusula sem esses literais opostos. Esse processo simplifica as cláusulas, reduzindo o problema até alcançar uma contraditoriedade ou a informação desejada.

### Etapas da Resolução

1. **Seleção de cláusulas:** Identifique duas cláusulas que contenham literais complementares, como `A` e `¬A`.
   
2. **Eliminação de literais:** Remova os literais complementares e una os restantes em uma nova cláusula.

3. **Repetição:** Continue o processo até que não seja possível resolver mais cláusulas ou se alcance uma cláusula vazia (contraditoriedade).

### Exemplo de Resolução

Considere as cláusulas abaixo:

- **Cláusula 1:** (A ∨ B)
- **Cláusula 2:** (¬A ∨ C)

A resolução segue estes passos:

1. Identifique os literais complementares: `(A)` e `(¬A)`.
2. Elimine os literais complementares e una os literais restantes: `(B ∨ C)`.
3. A cláusula resultante da resolução é:

   **Cláusula resolvida:** (B ∨ C)

### Aplicação em Provas

A resolução é usada para provar que uma sentença é consequência lógica de uma base de conhecimento. O método utiliza a **prova por refutação**, que consiste em:

1. Adicionar a negação da sentença à base de conhecimento.
2. Aplicar a resolução. Se ocorrer uma cláusula vazia, a sentença original é uma consequência lógica.

### Complexidade

O algoritmo de resolução é **completo**, mas possui alta **complexidade computacional**, especialmente em grandes bases de conhecimento, devido à explosão combinatória.

### Aplicações

- **Sistemas de Prova Automática:** Automatizam a demonstração de teoremas.
- **Sistemas de Diagnóstico:** Identificam falhas a partir de hipóteses e observações.
- **Agentes Baseados em Lógica:** Permitem que agentes deduzam informações sobre o ambiente, como no **Wumpus World**.

## Considerações Finais

O algoritmo de resolução é uma ferramenta poderosa para inferir novas informações e resolver problemas complexos. Apesar de sua alta complexidade, sua aplicabilidade em diversos domínios torna-o indispensável na inteligência artificial e em sistemas baseados em lógica.
