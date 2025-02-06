# Incerteza

A incerteza é uma característica inerente ao mundo real, manifestando-se em diversas áreas do conhecimento, como medicina, economia, direito e engenharia. Agentes inteligentes precisam lidar com essa incerteza, seja devido à observabilidade parcial do ambiente, ao comportamento não determinístico de sistemas complexos ou à influência de fatores imprevisíveis.

No contexto da previsão financeira, uma regra simples como:

`AltaTaxaJuros → QuedaInvestimentos`

não captura toda a complexidade envolvida. Nem sempre um aumento na taxa de juros resulta na redução dos investimentos, pois fatores como inflação, liquidez, confiança do mercado e políticas econômicas também influenciam esse cenário. Para representar melhor essa relação, poderíamos expandir a regra:

`AltaTaxaJuros → QuedaInvestimentos ∨ Estabilidade ∨ AumentoPoupança...`

No entanto, essa abordagem rapidamente se torna inviável por três razões principais:

1. **Complexidade**: Enumerar todas as possíveis condições e consequências é impraticável e computacionalmente inviável.  
2. **Limitações do conhecimento**: A ciência econômica, assim como outras áreas, nem sempre possui um entendimento completo sobre um fenômeno.  
3. **Falta de dados**: Mesmo quando há conhecimento teórico, a ausência de informações pode impedir previsões precisas.  

Criar um sistema logicamente exato exigiria regras extensas, detalhadas e, ainda assim, incompletas. Esse problema ocorre porque a incerteza surge tanto da **ignorância teórica** (a ciência pode não ter todas as respostas) quanto da **ignorância prática** (nem todas as informações estão disponíveis para um diagnóstico preciso).

## A Teoria da Probabilidade como Solução

A teoria da probabilidade oferece um meio eficaz para lidar com a incerteza, atribuindo um grau de crença numérico a diferentes eventos. Em vez de regras fixas, utilizamos probabilidades para expressar o conhecimento disponível. Por exemplo, na previsão financeira:

`P(QuedaInvestimentos | AltaTaxaJuros) = 0,6`

Isso indica que, com base nos dados disponíveis, há 60% de chance de que uma alta na taxa de juros leve à queda nos investimentos. Se novas informações forem obtidas, como um aumento na confiança do mercado, a probabilidade pode ser reavaliada:

`P(QuedaInvestimentos | AltaTaxaJuros, ConfiançaMercadoAlta) = 0,3`

Essa abordagem permite que os agentes ajustem suas crenças dinamicamente, considerando novas evidências e tornando a tomada de decisão mais robusta.

A principal diferença entre um agente lógico e um agente probabilístico está em seus compromissos epistemológicos. Um agente lógico opera com verdades absolutas (uma sentença é verdadeira, falsa ou desconhecida), enquanto um agente probabilístico trabalha com graus de crença entre 0 e 1, permitindo representar a incerteza de maneira mais realista.

## Aplicação no Mundo Real: O Problema do Smart Taxi

Imagine um agente de **Smart Taxi** encarregado de levar um passageiro ao aeroporto para um voo às 21h. O cliente precisa chegar até as 20h, e o agente conhece os seguintes fatos:

- O tempo médio de deslocamento é de **30 min** em trânsito médio, **45 min** em trânsito pesado e **20 min** em trânsito leve.  
- Entre **19h e 21h**, o trânsito é **médio**; entre **17h e 19h**, o trânsito é **pesado**.  
- Quando **chove**, o trânsito sempre se torna **pesado**.  
- Existe **50% de chance de chuva** no dia do voo.  
- Há **5% de chance de um acidente** na rota, aumentando o tempo em **10 min por acidente**.  
- Outras condições imprevisíveis podem impactar o trajeto.  

Um plano determinístico, assumindo trânsito médio, recomendaria sair **às 19h30**. No entanto, ao considerar incertezas como chuva e acidentes, essa estratégia se torna arriscada. A abordagem probabilística permite calcular o risco e sugerir uma alternativa mais segura, como sair às **19h** ou até antes, reduzindo a probabilidade de atrasos.

---

# Utilidade

No contexto do smart taxi, diversas soluções podem atender ao cliente, mas ele tem preferências específicas.  

A teoria da utilidade fornece uma abordagem quantitativa para modelar essas preferências e avaliar diferentes resultados.  

Segundo essa teoria, cada estado (ou sequência de estados) possui um valor de utilidade para um agente, e o agente buscará maximizar esse valor.  

A utilidade de um estado é subjetiva e depende do agente que a avalia.  

Uma função de utilidade pode ser construída considerando qualquer conjunto de critérios, sejam eles comuns ou peculiares, éticos ou questionáveis.

---

# Teoria de Decisão

A Teoria da Decisão busca aplicar princípios racionais à tomada de decisões em cenários complexos e de alto risco. Essa abordagem é amplamente utilizada em diversas áreas, como negócios, governo, direito, estratégia militar, diagnóstico médico, saúde pública, engenharia e gestão de recursos. O processo envolve a avaliação sistemática das opções disponíveis e de seus possíveis desdobramentos, considerando as preferências e prioridades do tomador de decisões.

## Papéis na Análise da Decisão
Na Análise da Decisão, tradicionalmente se destacam dois papéis principais:
1. **Tomador de Decisões**: Define suas preferências e estabelece prioridades entre os possíveis resultados.
2. **Analista de Decisão**: Identifica as alternativas disponíveis e os possíveis desdobramentos, utilizando as preferências do tomador de decisões para determinar a melhor escolha.

## Importância da Utilidade na Tomada de Decisão

Um dos desafios na análise de decisão é diferenciar a probabilidade da importância de um evento. No contexto médico, por exemplo, os primeiros sistemas especialistas classificavam diagnósticos apenas com base na probabilidade, o que podia levar a erros críticos. Doenças raras, mas altamente perigosas, poderiam ser subestimadas.

A incorporação do conceito de utilidade permite equilibrar a probabilidade de um diagnóstico com sua gravidade. Sistemas médicos modernos adotam essa abordagem para recomendar exames específicos e sugerir diagnósticos diferenciais, considerando não apenas a evidência disponível, mas também o valor das informações adquiridas.

## Evolução da Teoria da Decisão

A Teoria da Decisão continua a evoluir, sendo essencial para aprimorar processos automatizados e garantir que decisões – tomadas por humanos ou por sistemas inteligentes – sejam bem-informadas, racionais e alinhadas às necessidades específicas de cada situação.

---

# Notação Básica de Probabilidade

A notação em probabilidade é fundamental para entender e resolver problemas estatísticos. A seguir, apresentamos os principais símbolos e seus significados.

## Espaço Amostral
O **espaço amostral** (\(S\)) é o conjunto de todos os possíveis resultados de um experimento, representado por:

$$S = \{s_1, s_2, ..., s_n\}$$

**Exemplo:** No lançamento de um dado de seis faces:

$$S = \{1, 2, 3, 4, 5, 6\}$$

## Eventos
Um **evento** (\(E\)) é qualquer subconjunto do espaço amostral. Se o evento \(A\) representa a obtenção de um número par em um lançamento de dado, então:

$$A = \{2, 4, 6\}$$

## Probabilidade de um Evento
A probabilidade de um evento \(A\) ocorrer é dada por:

$$P(A) = \frac{|A|}{|S|}$$

onde \(|A|\) é o número de elementos no evento e \(|S|\) o total de elementos no espaço amostral.

**Exemplo:** A probabilidade de obter um número par ao lançar um dado justo:

$$P(A) = \frac{3}{6} = 0.5$$

## União e Interseção de Eventos
- A **união** de dois eventos \(A\) e \(B\), denotada por \(A \cup B\), inclui todos os elementos pertencentes a \(A\), \(B\) ou ambos.
- A **interseção** de \(A\) e \(B\), denotada por \(A \cap B\), contém os elementos comuns a ambos.

Se tivermos:

$$A = \{1, 2, 3\}, \quad B = \{3, 4, 5\}$$

então:

$$A \cup B = \{1, 2, 3, 4, 5\}$$  
$$A \cap B = \{3\}$$

## Eventos Mutuamente Exclusivos
Dois eventos \(A\) e \(B\) são mutuamente exclusivos se **não possuem elementos em comum**, ou seja:

$$A \cap B = \emptyset$$

**Exemplo:** No lançamento de um dado, os eventos "obter um número par" e "obter um número ímpar" são mutuamente exclusivos.

## Probabilidade Condicional
A **probabilidade condicional** de \(A\) dado \(B\) é representada por \(P(A|B)\) e definida como:

$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

desde que \(P(B) > 0\).

**Exemplo:** Em um baralho de 52 cartas, a probabilidade de escolher um rei (\(K\)), sabendo que já foi selecionada uma carta de figuras (J, Q ou K), é:

$$P(K|Figuras) = \frac{4/52}{12/52} = \frac{4}{12} = \frac{1}{3}$$

## Regra da Multiplicação
Para calcular a probabilidade de dois eventos \(A\) e \(B\) ocorrerem juntos, utilizamos:

$$P(A \cap B) = P(A) P(B|A)$$

Se \(A\) e \(B\) forem independentes:

$$P(A \cap B) = P(A) P(B)$$

---

# Independência e Independência Condicional

A independência entre variáveis em um modelo probabilístico é uma propriedade fundamental que simplifica significativamente a representação e o cálculo das distribuições conjuntas. Como destacado por Russell e Norvig (2022), quando variáveis são independentes, a distribuição conjunta pode ser fatorada, reduzindo o número de entradas necessárias para a sua especificação.

## Independência
Duas variáveis \( A \) e \( B \) são ditas **independentes** se o conhecimento do valor de uma não altera a probabilidade da outra. Matematicamente, isso é expresso como:

$$\[ P(A \cap B) = P(A) P(B) \]$$

Isso significa que o resultado de \( A \) não influencia o de \( B \), e vice-versa. Um exemplo clássico é o lançamento de duas moedas justas: o resultado de uma moeda não afeta o resultado da outra.

Russell e Norvig (2022) citam que a independência permite fatorar distribuições conjuntas. Por exemplo, se tivermos n lançamentos independentes de moedas, a distribuição conjunta pode ser escrita como:

$$\[ P(C_1, C_2, ..., C_n) = P(C_1) P(C_2) ... P(C_n) \]$$

## Independência Condicional
Em muitos casos, duas variáveis podem ser dependentes no geral, mas se tornarem **independentes quando condicionado a uma terceira variável**. Isso é chamado de **independência condicional**. Formalmente, \( A \) e \( B \) são condicionalmente independentes dado \( C \) se:

$$\[ P(A \cap B | C) = P(A | C) P(B | C) \]$$

Isso significa que, dado o conhecimento de \( C \), as variáveis \( A \) e \( B \) não fornecem mais informação uma sobre a outra.

## Importância e Limitações
A independência condicional é especialmente útil para simplificar modelos probabilísticos, como Redes Bayesianas, onde conexões indiretas entre variáveis podem ser eliminadas ao condicionar uma variável intermediária. No entanto, como ressaltado por Russell e Norvig (2022), a independência total entre variáveis é rara em problemas do mundo real. Mesmo quando subconjuntos de variáveis parecem independentes, podem existir relações complexas que exigem modelagens mais sofisticadas.

Portanto, entender a independência e a independência condicional é essencial para a construção de modelos probabilísticos eficientes e realistas.

---

# Regra de Bayes, aplicações e modelo ingênuo
# Redes Bayesianas
# Inferência
# Tempo e incerteza
# Estados e observações
# Modelo de transição e modelos de sensores
# Inferência em modelos temporais
## Filtragem
## Prediçao
## Suavização
## Explicação mais provável
## Aprendizado
# Modelo Oculto de Markov
# Filtros de Kalman



### referencias

ROUSSENQ, Fabiano Santos. TEORIA DA DECISÃO JUDICIAL EO USO DA INTELIGÊNCIA ARTIFICIAL. ARACÊ, v. 6, n. 4, p. 15052-15069, 2024.
