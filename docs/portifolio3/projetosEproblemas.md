# Alocação de recursos utilizando o AC-3

Neste problema, temos um cenário simples de alocação de recursos, onde o objetivo é alocar um conjunto de tarefas a um grupo de funcionários, respeitando as restrições de capacidade de trabalho e compatibilidade entre as tarefas e os funcionários. 

## Contexto do Problema:

- **Tarefas**: Temos três tarefas a serem alocadas: T1, T2 e T3. Cada uma delas exige um número específico de horas para ser concluída.
- **Funcionários**: Três funcionários estão disponíveis para realizar as tarefas: F1, F2 e F3. Cada funcionário possui uma capacidade máxima de horas que pode trabalhar em um determinado período.
  
## Restrições:

- Cada tarefa deve ser atribuída a exatamente um funcionário.
- A alocação deve respeitar a capacidade máxima de trabalho de cada funcionário, ou seja, um funcionário não pode ser alocado a uma tarefa que ultrapasse sua capacidade de horas.
- As tarefas não podem ser divididas entre funcionários. Ou seja, uma tarefa precisa ser completamente alocada a um único funcionário.

## Dados Específicos do Problema:

- **Tarefas**:
  - **T1**: 6 horas
  - **T2**: 8 horas
  - **T3**: 4 horas
- **Funcionários**:
  - **F1**: capacidade de 8 horas
  - **F2**: capacidade de 6 horas
  - **F3**: capacidade de 7 horas

## Objetivo:

Utilizando o algoritmo **AC-3**, o objetivo é garantir que os domínios de alocação de recursos (os funcionários que podem realizar as tarefas) sejam consistentes com as restrições de capacidade. O AC-3 será responsável por reduzir os domínios das variáveis de alocação (tarefa/funcionário) de forma a eliminar combinações inviáveis, assegurando que cada tarefa seja alocada corretamente a um funcionário sem exceder sua capacidade de trabalho.

## Código

```python

from collections import deque

# Definição das variáveis
tarefas = ['T1', 'T2', 'T3']
funcionarios = ['F1', 'F2', 'F3']
capacidades = {'F1': 8, 'F2': 6, 'F3': 7}
horas_necessarias = {'T1': 6, 'T2': 8, 'T3': 4}

# Definição dos domínios iniciais (todos os funcionários podem inicialmente pegar qualquer tarefa)
dominios = {
    'T1': ['F1', 'F2', 'F3'],
    'T2': ['F1', 'F2', 'F3'],
    'T3': ['F1', 'F2', 'F3']
}

# Função para verificar se o domínio de uma tarefa é consistente
def ac3(dominios, tarefas, funcionarios, capacidades, horas_necessarias):
    # Criação da fila de arcos (restrições entre as tarefas e os funcionários)
    fila = deque()
    for tarefa in tarefas:
        for funcionario in funcionarios:
            fila.append((tarefa, funcionario))

    # Processamento dos arcos
    while fila:
        tarefa, funcionario = fila.popleft()

        # Verifica se a tarefa pode ser alocada ao funcionário
        if funcionario in dominios[tarefa]:
            if horas_necessarias[tarefa] > capacidades[funcionario]:
                dominios[tarefa].remove(funcionario)
            
        # Reprocessar o arco caso o domínio tenha mudado
        for tarefa in tarefas:
            if funcionario in dominios[tarefa]:
                fila.append((tarefa, funcionario))
    
    return dominios

# Executando o AC-3
dominios_resultado = ac3(dominios, tarefas, funcionarios, capacidades, horas_necessarias)

# Exibindo os resultados
print("Domínios após o AC-3:")
for tarefa, dominio in dominios_resultado.items():
    print(f'{tarefa}: {dominio}')

```
## Explicação do código

### Definição das Variáveis:

- As tarefas (T1, T2, T3) e os funcionários (F1, F2, F3) são definidas como listas.
- As capacidades de trabalho dos funcionários e as horas necessárias para cada tarefa são armazenadas em dicionários.
- Inicialmente, todos os funcionários podem ser atribuídos a qualquer tarefa (domínios iniciais).

### Função ac3:

A função `ac3` começa criando uma fila de arcos, que representa as restrições entre tarefas e funcionários. Para cada arco, o algoritmo verifica se a alocação da tarefa a um funcionário é consistente com a restrição de capacidade (a tarefa não pode exigir mais horas do que o funcionário pode trabalhar). Caso uma tarefa não seja mais alocável a um funcionário devido à restrição de capacidade, o domínio dessa tarefa é atualizado.

### Resultado:

O algoritmo retorna os domínios finais de alocação de tarefas após aplicar o AC-3, garantindo que as alocações respeitem as restrições de capacidade.

### Resultado Esperado:

Após executar o código, o domínio final das alocações pode ser mostrado com a seguinte saída esperada:

foto com os resultados

Domínios após o AC-3:
T1: ['F1', 'F3']
T2: ['F1']
T3: ['F1', 'F2', 'F3']


### Interpretação do Resultado:

- **T1 (6 horas)**: A tarefa T1 pode ser alocada ao F1 ou F3, já que ambos têm capacidade suficiente para completá-la.
- **T2 (8 horas)**: A tarefa T2 pode ser alocada apenas ao F1, já que o F2 e o F3 não têm capacidade suficiente.
- **T3 (4 horas)**: A tarefa T3 pode ser alocada ao F1, F2 ou F3, pois todos têm capacidade para completá-la.

### Conclusão:

Neste exemplo prático de alocação de recursos, o AC-3 foi utilizado para reduzir os domínios de alocação das tarefas aos funcionários, garantindo que as alocações respeitem as restrições de capacidade de trabalho. O algoritmo ajudou a simplificar o problema, removendo combinações inviáveis e otimizando a alocação de recursos.

Este exemplo pode ser expandido para cenários mais complexos, com mais tarefas, funcionários e restrições adicionais.
