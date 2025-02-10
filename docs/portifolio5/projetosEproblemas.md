# Análise de risco de Crédito com Redes Bayesianas

A análise de risco de crédito é uma prática essencial para instituições financeiras, como bancos e cooperativas de crédito, com o objetivo de avaliar a probabilidade de inadimplência de um cliente. Essa avaliação é crucial para minimizar perdas financeiras e garantir a sustentabilidade da instituição.

O risco de crédito depende de vários fatores, como a situação financeira do cliente, seu histórico de crédito, sua renda e seu comportamento de pagamento. Métodos tradicionais de análise incluem modelos estatísticos e técnicas de aprendizado de máquina, mas eles podem ser limitados ao não considerar adequadamente a incerteza e a interdependência entre variáveis.

## Vantagens do Uso de Redes Bayesianas na Análise de Risco de Crédito

As redes bayesianas oferecem vantagens significativas na análise de risco de crédito, pois modelam incertezas e relações complexas entre variáveis. Entre os principais benefícios, destacam-se:

1. Modelagem de Incerteza
Redes bayesianas operam de forma probabilística, permitindo representar incertezas associadas a dados ausentes, ruídos e variabilidades na decisão de crédito. Por exemplo, é possível estimar a probabilidade de inadimplência mesmo quando algumas informações do cliente são imprecisas ou incompletas.

2. Capacidade de Representar Dependências entre Variáveis
Diferentemente de modelos tradicionais, as redes bayesianas capturam interdependências entre variáveis como idade, histórico de crédito e renda, permitindo uma análise mais realista do risco de inadimplência.

3. Inferência Probabilística
Com redes bayesianas, é possível calcular a probabilidade de inadimplência com base em um conjunto de evidências, como idade, renda e histórico de crédito. Isso possibilita decisões de crédito mais informadas e personalizadas.

4. Flexibilidade para Atualização com Novos Dados
As probabilidades nas redes bayesianas podem ser ajustadas dinamicamente à medida que novas informações são obtidas, tornando as previsões mais precisas ao longo do tempo.

5. Interpretação Intuitiva
As redes bayesianas são interpretáveis, tornando mais fácil compreender a influência das variáveis na probabilidade de inadimplência. Isso é essencial para transparência nas decisões de crédito e conformidade regulatória.

6. Capacidade de Lidar com Dados Incompletos ou Parciais
Redes bayesianas podem lidar com informações ausentes, inferindo valores prováveis com base em dados observados, o que as torna robustas para aplicações reais.

7. Integração de Conhecimento Especializado
As redes bayesianas permitem incorporar conhecimento especializado do setor financeiro, combinando dados históricos com estimativas de especialistas para melhorar a acurácia das previsões.

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
    
## Implementação

O código implementa uma Rede Bayesiana usando a biblioteca pgmpy para modelar o risco de inadimplência de um indivíduo com base em três fatores:

1. Idade (Jovem ou Adulto)
2. Histórico de Crédito (Bom ou Ruim)
3. Renda (Alta ou Baixa)

O objetivo é calcular a probabilidade de inadimplência com base nesses fatores usando inferência probabilística.


### Instalação necessária
```bash
pip install pgmpy tabulate colorama
```
### Código

```py
from pgmpy.models import BayesianNetwork
from pgmpy.factors.discrete import TabularCPD
from pgmpy.inference import VariableElimination
from tabulate import tabulate
from colorama import Fore, Style

# Definição da estrutura da Rede Bayesiana
model = BayesianNetwork([
    ('Idade', 'Inadimplencia'),
    ('Historico_Credito', 'Inadimplencia'),
    ('Renda', 'Inadimplencia')
])

# Definição das distribuições condicionais (CPDs)
cpd_idade = TabularCPD(variable='Idade', variable_card=2, values=[[0.7], [0.3]])  # 0: jovem, 1: adulto
cpd_historico_credito = TabularCPD(variable='Historico_Credito', variable_card=2, values=[[0.8], [0.2]])  # 0: bom, 1: ruim
cpd_renda = TabularCPD(variable='Renda', variable_card=2, values=[[0.6], [0.4]])  # 0: alta, 1: baixa

cpd_inadimplencia = TabularCPD(
    variable='Inadimplencia', variable_card=2,
    values=[[0.95, 0.85, 0.80, 0.40, 0.70, 0.50, 0.30, 0.10],  # Probabilidades de NÃO ser inadimplente
            [0.05, 0.15, 0.20, 0.60, 0.30, 0.50, 0.70, 0.90]], # Probabilidades de SER inadimplente
    evidence=['Idade', 'Historico_Credito', 'Renda'],
    evidence_card=[2, 2, 2]
)

# Adicionando as CPDs ao modelo
model.add_cpds(cpd_idade, cpd_historico_credito, cpd_renda, cpd_inadimplencia)

# Verificando se o modelo é válido
assert model.check_model()

# Criando o inferenciador
inference = VariableElimination(model)

# Função para calcular e exibir os resultados formatados
def calcular_inadimplencia(idade, historico_credito, renda):
    resultado = inference.query(
        variables=['Inadimplencia'],
        evidence={'Idade': idade, 'Historico_Credito': historico_credito, 'Renda': renda}
    )

    # Convertendo os valores para exibição
    valores = resultado.values
    dados = [
        ["Não Inadimplente (0)", f"{valores[0]:.2%}"],
        ["Inadimplente (1)", f"{valores[1]:.2%}"]
    ]

    # Exibindo os resultados
    print(Fore.CYAN + "\n========================================")
    print(f"🎯 Cenário: Idade={idade}, Histórico de Crédito={historico_credito}, Renda={renda}")
    print("========================================" + Style.RESET_ALL)
    print(tabulate(dados, headers=["Situação", "Probabilidade"], tablefmt="grid"))

# Testando diferentes cenários
cenarios = [
    (1, 0, 1),  # Adulto, Bom histórico de crédito, Baixa renda
    (0, 1, 1),  # Jovem, Histórico de crédito ruim, Baixa renda
    (1, 1, 0),  # Adulto, Histórico de crédito ruim, Alta renda
    (0, 0, 0),  # Jovem, Bom histórico de crédito, Alta renda
    (1, 1, 1),  # Adulto, Histórico de crédito ruim, Baixa renda
]

for cenario in cenarios:
    calcular_inadimplencia(*cenario)

```
**Explicação do Código:**

1. Criamos a estrutura da Rede Bayesiana, onde Inadimplência depende de Idade, Histórico de Crédito e Renda.
2. Definimos as distribuições condicionais (CPDs) para cada variável.
3. Validamos o modelo.
4. Criamos um algoritmo de inferência Bayesiana para calcular probabilidades condicionais.
5. Executamos cenários diferentes para entender como os fatores influenciam a inadimplência.

## Resultados

### Consulta 1
![image](https://github.com/user-attachments/assets/2152e8fa-f57b-4edb-a301-bef12b64efe3)

Neste cenário, temos:
- Idade = 1 (Adulto)
- Histórico de Crédito = 0 (Bom)
- Renda = 1 (Baixa)

A probabilidade de não inadimplência e inadimplência é exatamente 50% para cada.

Interpretação:

O modelo indica incerteza neste caso, pois os fatores se equilibram. Apesar do bom histórico de crédito (que reduz o risco de inadimplência), a renda baixa aumenta essa probabilidade. Como resultado, não há uma tendência clara, e o risco é dividido igualmente.

### Consulta 2
![image](https://github.com/user-attachments/assets/f57857c7-a99e-40fa-8078-a0989a0ed010)

Neste cenário, temos:
- Idade = 0 (Jovem)
- Histórico de Crédito = 1 (Ruim)
- Renda = 1 (Baixa)

A probabilidade de não inadimplência é 40%, enquanto a de inadimplência é 60%.

Interpretação:

Aqui, a inadimplência tem uma probabilidade maior do que a não inadimplência. Isso ocorre porque o indivíduo é jovem, tem um histórico de crédito ruim e uma renda baixa — todos esses fatores contribuem para um maior risco de não conseguir pagar suas dívidas.

### Consulta 3
![image](https://github.com/user-attachments/assets/e89b6140-fc5d-40df-a06d-1b3fb1c1e27c)

Neste cenário, temos:
- Idade = 1 (Adulto)
- Histórico de Crédito = 1 (Ruim)
- Renda = 0 (Alta)

A probabilidade de não inadimplência é 30%, enquanto a de inadimplência é 70%.

Interpretação:

Mesmo tendo renda alta, o fato de ter um histórico de crédito ruim pesa mais na análise. Isso sugere que a inadimplência passada ou o mau histórico financeiro são mais importantes para prever o risco de inadimplência do que o nível de renda atual.

### Consulta 4
![image](https://github.com/user-attachments/assets/e425e582-7750-4e5f-a4df-0116ddf425a2)

Neste cenário, temos:
- Idade = 0 (Jovem)
- Histórico de Crédito = 0 (Bom)
- Renda = 0 (Alta)

A probabilidade de não inadimplência é 95%, enquanto a de inadimplência é apenas 5%.

Interpretação:

Esse é o perfil mais seguro analisado. Um jovem com bom histórico de crédito e renda alta tem pouquíssima chance de se tornar inadimplente. Isso confirma que um bom histórico de crédito e uma renda confortável são os melhores indicadores para evitar inadimplência.

### Consulta 5
![image](https://github.com/user-attachments/assets/b7807f9a-b32c-405c-aeec-42b122727bf6)

Neste cenário, temos:
- Idade = 1 (Adulto)
- Histórico de Crédito = 1 (Ruim)
- Renda = 1 (Baixa)

A probabilidade de não inadimplência é 10%, enquanto a de inadimplência é 90%.

Interpretação:

Este é o perfil mais arriscado. A combinação de histórico de crédito ruim e baixa renda resulta em um risco altíssimo de inadimplência. Esse resultado sugere que instituições financeiras deveriam ter muita cautela ao conceder crédito para pessoas com esse perfil.

## Conclusão

Os resultados mostram como a interação entre idade, histórico de crédito e renda influencia a probabilidade de inadimplência.

Fatores mais impactantes:
1.  Histórico de Crédito: Ter um histórico ruim aumenta muito o risco de inadimplência, independentemente da idade ou renda.
2.  Renda: Uma renda baixa aumenta a probabilidade de inadimplência, mas não tanto quanto um histórico ruim.
3.  Idade: Ter idade adulta não garante segurança financeira, o histórico de crédito e a renda são mais relevantes.

Aplicação Prática: Bancos e financeiras podem usar esse modelo para avaliar melhor seus clientes e evitar concessões de crédito de alto risco.




