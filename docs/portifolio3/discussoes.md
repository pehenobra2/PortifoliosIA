# AC-3 (Algoritmo de Consistência de Arco)
O AC-3 é um algoritmo amplamente utilizado para resolver problemas de satisfação de restrições (PSR), sendo particularmente eficaz em redes de restrições com restrições binárias. Sua principal função é garantir a consistência de arco, ou seja, garantir que para cada variável em uma rede de restrições, todos os seus valores possíveis satisfaçam as restrições associadas com outras variáveis. O AC-3 é um algoritmo de propagação de restrições que aplica a consistência de arco de maneira eficiente, realizando uma série de verificações iterativas sobre as variáveis e suas relações até que não haja mais valores incompatíveis nos domínios das variáveis.

O funcionamento do AC-3 pode ser descrito como uma busca por inconsistências entre pares de variáveis, removendo os valores inválidos e propagando essas remoções por toda a rede. O algoritmo é baseado em uma estrutura de fila que contém os arcos que precisam ser verificados. A cada iteração, um arco é retirado da fila e as possíveis inconsistências entre as variáveis são verificadas, com valores sendo eliminados quando necessário. O processo continua até que todos os arcos sejam verificados e não haja mais mudanças nos domínios das variáveis.

## Exemplo prático

Vamos considerar o seguinte exemplo simples de um problema de coloração de mapas, onde temos três regiões (A, B e C) que precisam ser coloridas. As cores disponíveis são vermelho, azul e verde, e as restrições exigem que regiões adjacentes não possam ter a mesma cor. O objetivo é usar o algoritmo AC-3 para garantir que os domínios das variáveis (as cores das regiões) sejam consistentes com as restrições.

### Passo 1: Definindo as variáveis, domínios e restrições
- **Variáveis**: A, B, C
- **Domínios**: Cada variável pode ter um valor do conjunto {vermelho, azul, verde}.
- **Restrições**: A ≠ B, A ≠ C, B ≠ C (as regiões adjacentes não podem ter a mesma cor).

### Passo 2: Inicializando a fila de arcos
O primeiro passo do AC-3 é inicializar uma fila de arcos. Cada arco representa uma restrição entre duas variáveis. No nosso caso, temos três arcos:
- (A, B)
- (A, C)
- (B, C)

### Passo 3: Aplicando o AC-3

1. **Verificando o arco (A, B)**:
   - Para garantir a consistência de arco entre A e B, o algoritmo verifica se há algum valor no domínio de A que não tenha uma correspondência válida no domínio de B.
   - Suponha que A tenha inicialmente {vermelho, azul, verde} e B tenha {vermelho, azul}. Como A ≠ B, se A for vermelho, B não pode ser vermelho, então o domínio de B se reduz para {azul}. Se A for azul, B não pode ser azul, então o domínio de B se reduz para {vermelho}.
   - Se o domínio de B for alterado, o arco (A, B) precisa ser reprocessado, o que implica que o AC-3 verifica novamente o arco (B, A).

2. **Verificando o arco (A, C)**:
   - O mesmo processo é aplicado ao arco (A, C). O algoritmo verifica se, para cada valor no domínio de A, existe um valor correspondente no domínio de C que satisfaça a restrição A ≠ C.
   - Se o domínio de C for reduzido, o arco (A, C) também é reprocessado.

3. **Verificando o arco (B, C)**:
   - O algoritmo então verifica o arco (B, C), repetindo o mesmo processo de verificação e atualização dos domínios.

### Passo 4: Iteração e Terminação
O AC-3 continua processando os arcos até que não haja mais mudanças nos domínios das variáveis. Ou seja, quando nenhuma variável tem seu domínio reduzido, o algoritmo termina.

### Resultado
Ao final, o domínio de cada variável será reduzido para valores que são consistentes com as restrições. Por exemplo, se após a execução do AC-3 o domínio de A for {vermelho}, B for {azul}, e C for {verde}, significa que temos uma solução consistente para a coloração das regiões.

Neste exemplo, o AC-3 foi utilizado para reduzir os domínios das variáveis de forma que a solução do problema (a coloração do mapa) seja possível, respeitando as restrições de desigualdade entre as cores das regiões adjacentes.
