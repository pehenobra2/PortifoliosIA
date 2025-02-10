# Análise de risco de Crédito com Redes Bayesianas

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
