# Análise de risco de Crédito com Redes Bayesianas

A análise de risco de crédito é uma prática fundamental em instituições financeiras, como bancos e cooperativas de crédito, para avaliar a probabilidade de um cliente não pagar suas dívidas. Essa avaliação é crucial para a tomada de decisões sobre concessão de crédito, ajudando a minimizar perdas financeiras e a proteger a saúde da instituição.

O risco de crédito depende de uma série de fatores, como a situação financeira do cliente, seu histórico de crédito, sua renda, seu comportamento de pagamento anterior, entre outros. Tradicionalmente, métodos como análise estatística e modelos preditivos baseados em regressão ou aprendizado de máquina são usados para avaliar esse risco. No entanto, esses métodos podem ser limitados ao não considerar adequadamente a incerteza e a dependência entre variáveis.

## Por que usar Redes Bayesianas?

Redes bayesianas são modelos probabilísticos poderosos que permitem representar relações de dependência entre variáveis, especialmente quando há incerteza e a relação entre variáveis não é determinística. Elas são uma excelente escolha para a análise de risco de crédito por várias razões:

1. **Modelagem de Incerteza**: Redes bayesianas são capazes de lidar com incerteza explícita, permitindo modelar a probabilidade de um evento (como inadimplência) dado um conjunto de variáveis (como idade, histórico de crédito, e renda).
2. **Representação de Dependências**: Elas podem capturar as dependências entre diferentes variáveis de forma intuitiva. Por exemplo, a inadimplência pode depender de várias variáveis, como a renda, o histórico de crédito e a idade, e essas dependências podem ser modeladas de forma clara.
3. **Inferência Probabilística**: Uma das principais vantagens das redes bayesianas é a capacidade de realizar inferência probabilística. Ou seja, podemos calcular a probabilidade de um evento (como inadimplência) dado um conjunto de evidências (como dados do cliente). Isso é especialmente útil quando os dados são incompletos ou quando temos informações parciais sobre o cliente.
4. **Flexibilidade e Interpretabilidade**: As redes bayesianas são flexíveis, permitindo que você adicione ou remova variáveis facilmente, além de ser um modelo interpretável, o que é importante em contextos financeiros e regulatórios.

## Como usar Redes Bayesianas para Análise de Risco de Crédito?

Para utilizar redes bayesianas na análise de risco de crédito, o processo pode ser dividido em algumas etapas principais:

1. **Definir as Variáveis**: Primeiro, você precisa definir as variáveis que afetam o risco de crédito. Algumas variáveis comuns podem incluir:
  - Idade: Faixa etária do cliente.
  - Histórico de Crédito: Avaliação do histórico de pagamento do cliente.
  - Renda: Renda mensal ou anual do cliente.
  - Inadimplência: Se o cliente não pagou sua dívida (o alvo da análise).
2. **Construir a Estrutura da Rede**: Em seguida, você define como essas variáveis estão relacionadas. No caso do risco de crédito, a inadimplência pode depender diretamente da idade, histórico de crédito e renda. Essas relações podem ser representadas como arestas entre os nós (variáveis) na rede.
3. **Definir as Distribuições de Probabilidade (CPDs)**: As redes bayesianas exigem que você defina as distribuições de probabilidade condicionais para cada variável. Por exemplo, dado que o histórico de crédito de um cliente é ruim, qual a probabilidade de ele ser inadimplente? Essas distribuições podem ser baseadas em dados históricos ou estimativas.
4. **Inferir Probabilidades**: Depois de construir o modelo, você pode usar inferência bayesiana para calcular as probabilidades de inadimplência, dados outros fatores. A inferência permite que você determine a probabilidade de inadimplência de um cliente, dado seu perfil (idade, histórico de crédito, etc.), mesmo que nem todas as variáveis estejam completamente observadas.
5. **Tomada de Decisão**: Com as probabilidades calculadas, as instituições financeiras podem tomar decisões informadas sobre se devem ou não conceder crédito ao cliente, além de definir o limite de crédito apropriado e as taxas de juros.
    

Instale a biblioteca necessária:
```bash
pip install pgmpy
```

```py
from pgmpy.models import BayesianNetwork
from pgmpy.factors.discrete import TabularCPD
from pgmpy.inference import VariableElimination

# Definindo a estrutura da rede bayesiana
model = BayesianNetwork([('Idade', 'Inadimplencia'),
                         ('Historico_Credito', 'Inadimplencia'),
                         ('Renda', 'Inadimplencia')])

# Definindo as distribuições condicionais (CPD)
cpd_idade = TabularCPD(variable='Idade', variable_card=2,
                       values=[[0.7], [0.3]])  # 0: jovem, 1: adulto

cpd_historico_credito = TabularCPD(variable='Historico_Credito', variable_card=2,
                                   values=[[0.8], [0.2]])  # 0: bom, 1: ruim

cpd_renda = TabularCPD(variable='Renda', variable_card=2,
                       values=[[0.6], [0.4]])  # 0: alta, 1: baixa

cpd_inadimplencia = TabularCPD(variable='Inadimplencia', variable_card=2,
                               values=[[0.9, 0.7, 0.8, 0.3],
                                       [0.1, 0.3, 0.2, 0.7]],
                               evidence=['Idade', 'Historico_Credito', 'Renda'],
                               evidence_card=[2, 2, 2])

# Adicionando as CPDs ao modelo
model.add_cpds(cpd_idade, cpd_historico_credito, cpd_renda, cpd_inadimplencia)

# Verificando se o modelo é válido
assert model.check_model()

# Criando o inferenciador
inference = VariableElimination(model)

# Exemplo de inferência: qual é a probabilidade de inadimplência dado que a pessoa tem 30 anos (Idade = 1), tem um bom histórico de crédito (Historico_Credito = 0) e tem baixa renda (Renda = 1)?
probabilidade_inadimplencia = inference.query(variables=['Inadimplencia'],
                                              evidence={'Idade': 1, 'Historico_Credito': 0, 'Renda': 1})

print(probabilidade_inadimplencia)
```

Explicação do Código:
1. Modelo e Estrutura: A rede bayesiana é composta pelas variáveis Idade, Historico_Credito, Renda e Inadimplencia. A estrutura da rede define como essas variáveis se relacionam (por exemplo, a Inadimplencia depende de todas as outras variáveis).

2. Distribuições Condicionais (CPD): Para cada variável, definimos as distribuições condicionais (CPDs). As CPDs representam a probabilidade de uma variável, dado o estado das variáveis anteriores. Por exemplo, a probabilidade de inadimplência pode depender da idade, do histórico de crédito e da renda de uma pessoa.

3. Inferência: Usamos o inferenciador VariableElimination para calcular a probabilidade de inadimplência dado um conjunto de evidências (por exemplo, uma pessoa adulta, com bom histórico de crédito e baixa renda).

Como Funciona:
Ao rodar o código, o programa calculará a probabilidade de inadimplência dado que uma pessoa tem 30 anos, bom histórico de crédito e baixa renda. Isso pode ser útil na análise de risco de crédito para determinar a probabilidade de uma pessoa não pagar uma dívida com base em seu perfil.

Se precisar de ajustes no modelo ou na análise, ou se tiver mais variáveis para incluir, é só avisar!
