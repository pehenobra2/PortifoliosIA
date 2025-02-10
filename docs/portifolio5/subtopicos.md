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
O **espaço amostral** $((S))$ é o conjunto de todos os possíveis resultados de um experimento, representado por:

$$S = \{s_1, s_2, ..., s_n\}$$

**Exemplo:** No lançamento de um dado de seis faces:

$$S = \{1, 2, 3, 4, 5, 6\}$$

## Eventos
Um **evento** $((E))$ é qualquer subconjunto do espaço amostral. Se o evento $(A)$ representa a obtenção de um número par em um lançamento de dado, então:

$$A = \{2, 4, 6\}$$

## Probabilidade de um Evento
A probabilidade de um evento $(A)$ ocorrer é dada por:

$$P(A) = \frac{|A|}{|S|}$$

onde $(|A|)$ é o número de elementos no evento e $(|S|)$ o total de elementos no espaço amostral.

**Exemplo:** A probabilidade de obter um número par ao lançar um dado justo:

$$P(A) = \frac{3}{6} = 0.5$$

## União e Interseção de Eventos
- A **união** de dois eventos $(A)$ e $(B)$, denotada por $(A \cup B)$, inclui todos os elementos pertencentes a $(A)$, $(B)$ ou ambos.
- A **interseção** de $(A)$ e $(B)$, denotada por $(A \cap B)$, contém os elementos comuns a ambos.

Se tivermos:

$$A = \{1, 2, 3\}, \quad B = \{3, 4, 5\}$$

então:

$$A \cup B = \{1, 2, 3, 4, 5\}$$  
$$A \cap B = \{3\}$$

## Eventos Mutuamente Exclusivos
Dois eventos $(A)$ e $(B)$ são mutuamente exclusivos se **não possuem elementos em comum**, ou seja:

$$A \cap B = \emptyset$$

**Exemplo:** No lançamento de um dado, os eventos "obter um número par" e "obter um número ímpar" são mutuamente exclusivos.

## Probabilidade Condicional
A **probabilidade condicional** de $(A)$ dado $(B)$ é representada por $(P(A|B))$ e definida como:

$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

desde que $(P(B) > 0)$.

**Exemplo:** Em um baralho de 52 cartas, a probabilidade de escolher um rei $((K))$, sabendo que já foi selecionada uma carta de figuras (J, Q ou K), é:

$$P(K|Figuras) = \frac{4/52}{12/52} = \frac{4}{12} = \frac{1}{3}$$

## Regra da Multiplicação
Para calcular a probabilidade de dois eventos $(A)$ e $(B)$ ocorrerem juntos, utilizamos:

$$P(A \cap B) = P(A) P(B|A)$$

Se $(A)$ e $(B)$ forem independentes:

$$P(A \cap B) = P(A) P(B)$$

---

# Independência e Independência Condicional

A independência entre variáveis em um modelo probabilístico é uma propriedade fundamental que simplifica significativamente a representação e o cálculo das distribuições conjuntas. Como destacado por Russell e Norvig (2022), quando variáveis são independentes, a distribuição conjunta pode ser fatorada, reduzindo o número de entradas necessárias para a sua especificação.

## Independência
Duas variáveis $( A )$ e $( B )$ são ditas **independentes** se o conhecimento do valor de uma não altera a probabilidade da outra. Matematicamente, isso é expresso como:

$$\[ P(A \cap B) = P(A) P(B) \]$$

Isso significa que o resultado de $( A )$ não influencia o de $( B )$, e vice-versa. Um exemplo clássico é o lançamento de duas moedas justas: o resultado de uma moeda não afeta o resultado da outra.

Russell e Norvig (2022) citam que a independência permite fatorar distribuições conjuntas. Por exemplo, se tivermos n lançamentos independentes de moedas, a distribuição conjunta pode ser escrita como:

$$\[ P(C_1, C_2, ..., C_n) = P(C_1) P(C_2) ... P(C_n) \]$$

## Independência Condicional
Em muitos casos, duas variáveis podem ser dependentes no geral, mas se tornarem **independentes quando condicionado a uma terceira variável**. Isso é chamado de **independência condicional**. Formalmente, $( A )$ e $( B )$ são condicionalmente independentes dado $( C )$ se:

$$\[ P(A \cap B | C) = P(A | C) P(B | C) \]$$

Isso significa que, dado o conhecimento de $( C )$, as variáveis $( A )$ e $( B )$ não fornecem mais informação uma sobre a outra.

## Importância e Limitações
A independência condicional é especialmente útil para simplificar modelos probabilísticos, como Redes Bayesianas, onde conexões indiretas entre variáveis podem ser eliminadas ao condicionar uma variável intermediária. No entanto, como ressaltado por Russell e Norvig (2022), a independência total entre variáveis é rara em problemas do mundo real. Mesmo quando subconjuntos de variáveis parecem independentes, podem existir relações complexas que exigem modelagens mais sofisticadas.

Portanto, entender a independência e a independência condicional é essencial para a construção de modelos probabilísticos eficientes e realistas.

---

# Regra de Bayes, Aplicações e Modelo Bayesiano Ingênuo

A **Regra de Bayes** é um dos pilares da inferência probabilística e desempenha um papel fundamental nos sistemas modernos de Inteligência Artificial (IA). Derivada do teorema formulado por **Thomas Bayes**, essa regra permite atualizar probabilidades à medida que novas evidências são incorporadas. Em sua forma geral, a Regra de Bayes é expressa como:

$$ P(A | B) = \frac{P(B | A) P(A)}{P(B)} $$

Onde:
- $( P(A | B) )$ é a **probabilidade a posteriori**, ou seja, a probabilidade de $(A)$ ocorrer dado que $(B)$ já ocorreu;
- $( P(B | A) )$ é a **probabilidade condicional** de $(B)$ ocorrer dado que $(A)$ ocorreu;
- $( P(A) )$ é a **probabilidade a priori** de $(A)$;
- $( P(B) )$ é a **probabilidade total** de $(B)$.

## Aplicação da Regra de Bayes

A Regra de Bayes é amplamente aplicada em diversos domínios, como diagnóstico médico, filtragem de spam e reconhecimento de padrões. Um exemplo clássico de sua aplicação é no **diagnóstico médico**. Suponha que um médico queira determinar a probabilidade de um paciente ter meningite com base no sintoma de rigidez no pescoço. Sabemos que:

- A meningite causa rigidez no pescoço em 70% dos casos $((P(S | M) = 0,7))$;
- A probabilidade a priori de um paciente ter meningite é de 1 em 50.000 $((P(M) = 0,00002\))$;
- A probabilidade de qualquer paciente apresentar rigidez no pescoço, independentemente da causa, é de 1% $((P(S) = 0,01))$.

Aplicando a **Regra de Bayes**, obtemos:

$$ P(M | S) = \frac{P(S | M) P(M)}{P(S)} = \frac{(0,7)(0,00002)}{0,01} = 0,0014 $$

Ou seja, mesmo que a rigidez no pescoço seja um sintoma comum da meningite, a **probabilidade real de um paciente com esse sintoma ter meningite é de apenas 0,14%**. Esse exemplo ilustra como a Regra de Bayes equilibra evidências e probabilidades prévias, fornecendo uma base sólida para tomadas de decisão mais precisas. **Segundo Russell & Norvig (2022), capítulo 13.5**, a Regra de Bayes é essencial em contextos como o diagnóstico médico, pois ela permite calcular a probabilidade de uma condição (como a meningite) dada uma evidência observada (como a rigidez no pescoço), equilibrando informações causais e probabilísticas de maneira eficiente.

## O Modelo Bayesiano Ingênuo

O **modelo bayesiano ingênuo** é uma simplificação da Regra de Bayes, amplamente utilizado em **aprendizado de máquina e classificação de dados**. Ele assume que as variáveis preditoras são **condicionalmente independentes**, dado o valor da variável de classe. A equação do modelo pode ser expressa como:

$$ P(C | X_1, X_2, ..., X_n) = \frac{P(C) \prod_{i=1}^{n} P(X_i | C)}{P(X_1, X_2, ..., X_n)} $$

Onde $(C)$ representa a **classe** e $(X_i)$ são os **atributos observados**.

Esse modelo é amplamente empregado na **classificação de textos**, como na **filtragem de spam**. Um classificador bayesiano ingênuo pode aprender a distinguir e-mails legítimos de spam analisando a frequência das palavras nas mensagens. Embora a suposição de independência condicional seja uma simplificação que nem sempre é verdadeira na prática, esse modelo frequentemente oferece bons resultados em diversas aplicações. **Como observado por Costa et al. (2013)**, o modelo bayesiano ingênuo é eficaz mesmo quando as variáveis preditoras não são estritamente independentes.

---

# Redes Bayesianas

As **Redes Bayesianas** são ferramentas poderosas para modelar incertezas e dependências entre variáveis em sistemas complexos. Elas são representações gráficas probabilísticas compostas por **grafos direcionados acíclicos (DAGs)**, nos quais:

- Os **nós** representam variáveis aleatórias;
- As **arestas** indicam relações de dependência causal entre as variáveis;
- A força dessas relações é quantificada por **probabilidades condicionais**.

Essas redes foram inspiradas pela teoria de **Thomas Bayes**, um reverendo presbiteriano do século XVIII, cujas ideias sobre probabilidades condicionais e a influência de eventos passados nas probabilidades de eventos futuros deram origem a uma revolução em várias áreas do conhecimento, desde a genética até a teologia (PENA, 2006). 

Bayes formulou uma abordagem matemática para calcular probabilidades a partir de informações parciais ou incertas, estabelecendo que **eventos passados alteram a probabilidade de ocorrência de eventos correlacionados no futuro**. Essa teoria tem aplicações significativas, especialmente em cenários onde a certeza é difícil de alcançar, como em diagnósticos médicos, tomada de decisões financeiras e análise de risco (COSTA et al., 2013). Seu raciocínio nos ensina que, ao aplicar as probabilidades condicionais, podemos entender melhor as interações complexas entre variáveis.

## Estrutura das Redes Bayesianas

Em uma rede bayesiana, as **probabilidades condicionais** são representadas por distribuições de probabilidade associadas a cada nó. Essas distribuições capturam como as variáveis dependem das outras. A construção de uma rede envolve três etapas principais: definir as variáveis relevantes, estabelecer as relações de dependência causal entre elas e atribuir probabilidades condicionais adequadas (NORVIG; RUSSEL, 2004).

Como exemplo, consideremos uma situação médica: a probabilidade de uma mulher com mais de 40 anos estar com câncer de mama após um exame de mamografia. Nesse contexto, a probabilidade de um diagnóstico positivo para câncer é influenciada não apenas pela precisão do exame, mas também pela probabilidade pré-existente de que a mulher tenha câncer (PENA, 2006). A utilização de uma rede bayesiana permite calcular a probabilidade de a mulher realmente ter a doença, após o exame positivo, levando em conta tanto a precisão do teste quanto a probabilidade de câncer na população em geral.

Esse raciocínio pode ser expresso pela fórmula de Bayes:

$$\[ Pr(A|B) = \frac{Pr(B|A) \cdot Pr(A)}{Pr(B)} \]$$

onde $\(Pr(A)\)$ e $\(Pr(B)\)$ são as probabilidades a priori dos eventos A e B, enquanto $\(Pr(B|A)\)$ e $\(Pr(A|B)\)$ representam as probabilidades condicionais.

## Exemplos Práticos de Aplicação

As redes bayesianas têm diversas aplicações, especialmente quando se trata de decisões baseadas em incertezas. Alguns exemplos incluem:

- **Diagnóstico médico**: Como o diagnóstico de apneia do sono ou câncer de mama, onde múltiplas variáveis influenciam a probabilidade de uma condição, como a idade, histórico familiar e resultados de exames (PENA, 2006).
  
- **Análise de risco de crédito**: Em que variáveis como o histórico de crédito, o tempo de emprego e o valor do empréstimo determinam a probabilidade de inadimplência de um solicitante.

- **Classificação de imagens**: Como a análise de imagens de satélite para identificar diferentes tipos de superfícies, como vegetação ou áreas urbanas, usando probabilidades condicionais para associar características a classes específicas.

Dessa forma, as redes bayesianas não apenas fornecem uma maneira eficaz de lidar com a incerteza, mas também permitem modelar as interações entre as variáveis de forma clara e concisa. Ao aplicar o raciocínio bayesiano, muitas vezes nos deparamos com resultados que desafiam o senso comum, como exemplificado pelo **Problema de Monty Hall**. Esse tipo de análise é fundamental para entender como as probabilidades podem ser contraintuitivas, mas ainda assim racionais e fundamentadas nas condições oferecidas.

---

# Inferência

A inferência é um processo fundamental na inteligência artificial, especialmente no contexto das redes probabilísticas, como as redes bayesianas. Ela consiste em deduzir informações sobre variáveis de interesse com base em evidências observadas. Neste texto, exploraremos dois tipos principais de inferência em redes bayesianas, conforme descrito no livro de Russell e Norvig.

## Inferência por Enumeração

A **inferência por enumeração** é uma abordagem direta para calcular a probabilidade de uma variável, considerando todas as possíveis combinações de valores das variáveis na rede. Esse processo envolve a soma das probabilidades das diferentes combinações, levando em conta as probabilidades condicionais associadas.

Em redes bayesianas, a inferência por enumeração pode ser realizada por meio de técnicas como a **eliminação de variáveis** ou **enumeração exaustiva**. Nesse método, as combinações de valores das variáveis são avaliadas sistematicamente para calcular a probabilidade marginal de uma variável de interesse.

Embora seja uma abordagem exata e relativamente simples de entender, a inferência por enumeração enfrenta limitações significativas quando aplicada a redes grandes. O número de combinações possíveis cresce exponencialmente à medida que o número de variáveis aumenta, tornando o processo computacionalmente caro e, em muitos casos, inviável para redes complexas.

## Inferência Aproximada em Redes Bayesianas

Quando a inferência por enumeração se torna impraticável devido ao alto custo computacional, recorre-se à **inferência aproximada**. Em vez de calcular todas as possíveis combinações, essa abordagem utiliza métodos probabilísticos para obter uma estimativa eficiente das distribuições de probabilidade.

Entre as técnicas mais comuns de inferência aproximada, destacam-se:

- **Amostragem de Monte Carlo**: Este método envolve gerar várias amostras das variáveis de interesse e usar essas amostras para estimar a distribuição de probabilidade das variáveis. Uma variante poderosa dessa técnica é a **cadeia de Markov Monte Carlo (MCMC)**, que permite gerar amostras de distribuições complexas por meio de um processo iterativo.

- **Propagação de Crença**: Embora seja mais comumente associada a redes de Markov, a **propagação de crença** também pode ser aplicada em redes bayesianas. Nesse processo, as informações são propagadas pela rede para atualizar as probabilidades das variáveis à medida que novas evidências são incorporadas. O objetivo é ajustar as crenças sobre as variáveis, com base nas informações mais recentes.

Essas técnicas de inferência aproximada são vantajosas porque permitem obter boas estimativas das distribuições de probabilidade com um custo computacional consideravelmente menor do que o exigido pela enumeração exaustiva. Assim, elas tornam viáveis a inferência em redes bayesianas mais complexas.

---

# Tempo e incerteza

Problemas dinâmicos envolvem variáveis que mudam ao longo do tempo, o que introduz uma camada de complexidade no raciocínio probabilístico. Ao contrário de cenários estáticos, como o diagnóstico de um carro, onde as variáveis são tratadas como fixas, problemas como o monitoramento de um paciente diabético exigem considerar as mudanças temporais. Por exemplo, os níveis de açúcar no sangue de um paciente podem variar devido a fatores como alimentação, insulina e atividade física, o que demanda a modelagem dessas mudanças para avaliar o estado atual e prever os efeitos de ações futuras (Russell & Norvig, 2022).

Esse conceito se aplica a diversas áreas, como o rastreamento de robôs ou a interpretação de sequências de palavras faladas. A incerteza temporal deve ser considerada para fazer predições e decisões adequadas. Modelos como Markov e Filtros de Kalman são úteis para lidar com essa incerteza, permitindo a estimativa de estados em sistemas dinâmicos (Russell & Norvig, 2022).

---

# Estados e observações

No raciocínio probabilístico dinâmico, o mundo é modelado como uma sequência de fatias de tempo, onde cada fatia contém variáveis, algumas observáveis e outras não. O conjunto de variáveis de estado em cada fatia é representado por $(X_t)$, enquanto o conjunto de variáveis observáveis é representado por $(E_t)$, com a observação no tempo $(t)$ sendo $(E_t = e_t)$ para algum conjunto de valores $(e_t)$ (Russell & Norvig, 2022).

Por exemplo, em um cenário de segurança, um guarda pode observar se o diretor entra com ou sem guarda-chuva. A variável de evidência $(E_t)$ seria se o guarda-chuva está presente ou não, enquanto a variável de estado $(X_t)$ representaria se está chovendo. Em contextos mais complexos, como o monitoramento de diabetes, variáveis de evidência podem incluir medições de açúcar no sangue e a pulsação, e variáveis de estado podem representar o nível de açúcar no sangue e o conteúdo do estômago (Russell & Norvig, 2022).

A modelagem do tempo entre as fatias também depende do problema. Para o monitoramento de diabetes, o intervalo pode ser de uma hora, ao invés de um dia, o que implica na consideração do tempo como uma sequência discreta de eventos. A notação $(X_{a:b})$ denota o conjunto de variáveis desde $(X_a)$ até $(X_b)$, ajudando a organizar o tempo e as observações de maneira estruturada (Russell & Norvig, 2022).


---

# Modelo de transição e modelos de sensores

A modelagem do mundo, no contexto de raciocínio probabilístico dinâmico, envolve dois componentes fundamentais: o **modelo de transição** e o **modelo de sensores**.

## Modelo de transição

O modelo de transição descreve como o estado do mundo evolui ao longo do tempo, representado pela distribuição de probabilidade $\(P(X_t | X_{0:t-1})\)$, que depende dos estados anteriores. Para lidar com a complexidade de estados passados ilimitados, adota-se a **suposição de Markov**, que limita a dependência do estado atual a um número fixo e finito de estados anteriores. No caso de um processo de Markov de primeira ordem, a transição entre estados é modelada por $\(P(X_t | X_{t-1})\)$, simplificando a descrição da evolução do sistema ao longo do tempo.

Embora essa abordagem seja eficaz em muitos cenários, ela pode não ser completamente precisa. Por exemplo, na previsão de chuva, o estado do dia anterior pode não ser suficiente para prever com exatidão as condições do tempo. Para aprimorar a modelagem, é possível aumentar a ordem do processo de Markov, incluindo mais estados passados, ou expandir o conjunto de variáveis de estado, incorporando fatores como temperatura e umidade. Essas modificações podem resultar em previsões mais acuradas e representações mais completas do sistema.

## Modelos de sensores

O **modelo de sensores** trata da obtenção de evidências a partir do estado atual. Ele descreve como as variáveis de evidência $E_t$ são geradas pelo estado $X_t$, representado pela distribuição $(P(E_t | X_t)\)$. No exemplo do tempo, o estado do clima (por exemplo, se está chovendo) afeta diretamente a observação de um guarda-chuva. A relação entre o estado real do mundo e as observações feitas pelos sensores é crucial para inferir o estado do sistema a partir das evidências coletadas.

Para que a modelagem seja completa, é necessário também especificar a distribuição de probabilidade inicial $(P(X_0))$, além dos modelos de transição e de sensores para cada etapa subsequente. Com esses componentes definidos, é possível construir uma representação precisa da evolução e observação do mundo ao longo do tempo, um requisito essencial para sistemas baseados em raciocínio probabilístico dinâmico.

---

# Inferência em modelos temporais

Ao trabalhar com modelos temporais, uma vez definida a estrutura básica do modelo, as tarefas principais de inferência que precisam ser resolvidas incluem **filtragem**, **previsão**, **suavização**, **explicação mais provável** e **aprendizado**.

## Filtragem

A **filtragem** é o processo de calcular o estado de crença — ou seja, a distribuição posterior sobre o estado mais recente — com base nas evidências coletadas até o momento. Em termos práticos, a tarefa consiste em calcular $P(X_t | e_{1:t})$, que representa a probabilidade de um evento, como a chuva, dado que observamos um guarda-chuva. A filtragem permite que um agente racional mantenha o controle sobre o estado atual, essencial para a tomada de decisões informadas. Além disso, um cálculo semelhante pode ser realizado para determinar a probabilidade da sequência de evidências $P(e_{1:t})$.

## Previsão

A **previsão** envolve o cálculo da distribuição posterior sobre o estado futuro, com base nas evidências acumuladas até o momento. Ou seja, é necessário calcular $P(X_{t+k} | e_{1:t})$ para algum $k > 0$. No exemplo do guarda-chuva, isso poderia significar calcular a probabilidade de chuva daqui a três dias, com base nas observações do portador de guarda-chuva até o momento. A previsão é útil para avaliar possíveis cursos de ação, levando em consideração os resultados esperados para o futuro.

## Suavização

A **suavização** se refere ao cálculo da distribuição posterior de um estado passado, levando em consideração todas as evidências até o presente. Nesse caso, o objetivo é calcular $P(X_k | e_{1:t})$ para algum $k$ tal que $0 \leq k < t$. No exemplo do guarda-chuva, isso poderia significar calcular a probabilidade de que tenha chovido em um dia passado, como na quarta-feira passada, com base nas observações realizadas até hoje. A suavização é útil porque oferece uma estimativa mais precisa do estado passado do que a disponível no momento em que o evento ocorreu, uma vez que incorpora evidências adicionais.

## Explicação mais provável

A **explicação mais provável** refere-se à tarefa de identificar a sequência de estados que mais provavelmente gerou uma sequência de observações. Em outras palavras, o objetivo é calcular $P(x_{1:t} | e_{1:t})$. No caso do exemplo do guarda-chuva, isso significaria que, dado que o guarda-chuva foi observado nos três primeiros dias e não foi observado no quarto, a explicação mais provável seria a de que choveu nos três primeiros dias e não choveu no quarto. Esse tipo de algoritmo é útil em diversas aplicações, como o reconhecimento de fala, no qual o objetivo é determinar a sequência de palavras mais provável a partir de uma série de sons, ou na reconstrução de dados transmitidos sobre um canal ruidoso.

## Aprendizado

O **aprendizado** envolve a adaptação dos modelos de transição e sensores, caso esses ainda não sejam conhecidos, a partir das observações feitas. Assim como nas redes bayesianas estáticas, o aprendizado em redes bayesianas dinâmicas pode ser realizado como um subproduto da inferência. Durante a inferência, obtemos uma estimativa de quais transições ocorreram e quais estados geraram as leituras dos sensores. Essas estimativas podem ser usadas para atualizar os modelos, e o processo é iterativo até que a convergência seja alcançada. Esse processo é um exemplo de maximização de expectativas, ou algoritmo EM.

É importante destacar que o aprendizado exige a inferência por suavização total, e não por filtragem. A suavização oferece melhores estimativas dos estados, o que é fundamental para garantir a convergência correta do aprendizado. Por exemplo, em uma investigação criminal, a suavização será necessária para deduzir o que aconteceu, uma vez que, a menos que haja testemunhas, a filtragem sozinha não seria suficiente para fornecer informações precisas sobre eventos passados.


---

# Modelo Oculto de Markov

Os Modelos Ocultos de Markov (MOMs) oferecem uma abordagem probabilística para modelagem temporal, na qual o estado do sistema é representado por uma única variável aleatória discreta. Cada estado possível do mundo corresponde a um valor específico dessa variável. O exemplo do guarda-chuva, discutido anteriormente, é um MOM, pois depende exclusivamente da variável "Chuva".

Quando um sistema apresenta múltiplas variáveis de estado, ainda é possível representá-lo como um MOM, combinando todas essas variáveis em uma única "megavariável", cujos valores representam todas as possíveis combinações dos estados individuais. Essa estrutura compacta permite a implementação eficiente dos principais algoritmos de inferência utilizando matrizes.

## Algoritmos Matriciais Simplificados

A estrutura dos MOMs permite representar o modelo de transição entre estados e o modelo de sensores de forma matricial, o que torna os cálculos mais eficientes e facilita a implementação dos algoritmos fundamentais de inferência.

Com um único estado discreto $X_t$, podemos representar suas possíveis configurações como inteiros de $1$ a $S$, onde $S$ é o número total de estados possíveis. O modelo de transição, que descreve as probabilidades de mudança entre estados ao longo do tempo, é expresso como uma matriz de transição $T$ de dimensão $S \times S$:

$$T_{ij} = P(X_t = j \mid X_{t-1} = i)$$

onde $T_{ij}$ representa a probabilidade de transição do estado $i$ para o estado $j$.

Além disso, os MOMs incluem um modelo de observação, que define a relação entre os estados ocultos e as observações emitidas. Este modelo é representado por uma matriz de observação $O$ de dimensão $S \times M$:

$$O_{jk} = P(O_t = k \mid X_t = j)$$

onde $O_{jk}$ representa a probabilidade de observar a saída $k$ dado que o sistema está no estado $j$, e $M$ é o número total de observações possíveis.

### Algoritmos Fundamentais

Os principais algoritmos utilizados para inferência em MOMs incluem:

1. **Algoritmo Forward (Propagação para Frente)**: Calcula a distribuição de probabilidade sobre os estados ocultos dados as observações até o tempo atual. Utiliza a relação:
   
   $$\alpha_t(j) = P(O_1, O_2, ..., O_t, X_t = j)$$
   
   Pode ser calculado recursivamente por:
   
   $$\alpha_t(j) = \sum_{i=1}^{S} \alpha_{t-1}(i) T_{ij} O_{jk}$$

2. **Algoritmo Backward (Propagação para Trás)**: Similar ao algoritmo forward, mas calcula a probabilidade das observações futuras dadas um estado atual.
   
   $$\beta_t(i) = P(O_{t+1}, O_{t+2}, ..., O_T \mid X_t = i)$$
   
   A recursão segue:
   
   $$\beta_t(i) = \sum_{j=1}^{S} T_{ij} O_{jk} \beta_{t+1}(j)$$

3. **Algoritmo de Viterbi**: Utilizado para encontrar a sequência mais provável de estados ocultos dados uma sequência de observações. Baseia-se na recursão:
   
   $$\delta_t(j) = \max_{i} \left( \delta_{t-1}(i) T_{ij} \right) O_{jk}$$
   
   Esse algoritmo é amplamente utilizado para decodificação de sequências ocultas em aplicações como reconhecimento de fala e biologia computacional.

### Aplicações dos Modelos Ocultos de Markov

Os MOMs são amplamente utilizados em diversas áreas, como:

- **Processamento de Linguagem Natural (PLN)**: Para modelagem de sequências de palavras e reconhecimento de fala.
- **Biologia Computacional**: Para análise de sequências de DNA e predição de estruturas proteicas.
- **Financeiro**: Para modelagem de séries temporais e previsão de mercados.
- **Robótica**: Para navegação e aprendizado baseado em observações ruidosas.

A eficiência e flexibilidade dos Modelos Ocultos de Markov fazem deles uma ferramenta essencial para modelagem probabilística em diversas disciplinas.

---

# Filtro de Kalman

O Filtro de Kalman é um algoritmo recursivo que permite estimar o estado de um sistema dinâmico a partir de medições ruidosas. Ele é amplamente utilizado em engenharia, controle de sistemas, robótica, economia e diversas outras áreas devido à sua capacidade de fornecer estimativas precisas mesmo na presença de incerteza.

## Fundamentos do Filtro de Kalman

O Filtro de Kalman baseia-se em um modelo matemático que descreve a evolução do estado do sistema ao longo do tempo. Esse modelo é composto por:

1. **Equação de Estado**: Define a transição do estado do sistema de um instante para o próximo:
   
   $$x_k = A x_{k-1} + B u_k + w_k$$
   
   onde:
   - $x_k$ representa o estado do sistema no instante $k$,
   - $A$ é a matriz de transição de estado,
   - $B$ é a matriz de controle (se houver um controle externo $u_k$),
   - $w_k$ é o ruído do processo, assumido como uma variável aleatória Gaussiana.

2. **Equação de Observação**: Relaciona o estado verdadeiro do sistema com a medição realizada:
   
   $$z_k = H x_k + v_k$$
   
   onde:
   - $z_k$ é a medição realizada,
   - $H$ é a matriz de observação,
   - $v_k$ representa o ruído da medição, também assumido como Gaussiano.

## Ciclo de Funcionamento do Filtro de Kalman

O Filtro de Kalman opera de forma iterativa em dois passos principais:

1. **Previsão (Predição)**: Estima o estado futuro do sistema e a incerteza associada.

2. **Atualização (Correção)**: Ajusta a estimativa com base na nova medição.

## Aplicações do Filtro de Kalman

O Filtro de Kalman é utilizado em diversas aplicações, como:

- **Navegação e Controle de Veículos**: Estima a posição e velocidade de veículos autônomos e espaçonaves.
- **Processamento de Sinais**: Redução de ruído e filtragem em sinais digitais.
- **Economia e Finanças**: Previsão de séries temporais e modelagem de dados financeiros.
- **Robótica**: Localização e mapeamento de robôs móveis em ambientes dinâmicos.

A principal vantagem do Filtro de Kalman é sua eficiência computacional, tornando-o ideal para sistemas em tempo real. Além disso, sua formulação probabilística permite lidar com incertezas de maneira robusta, garantindo estimativas confiáveis mesmo com medições imperfeitas.

Assim, o Filtro de Kalman continua sendo uma ferramenta essencial em diversos campos, oferecendo soluções eficientes para problemas de rastreamento e predição em sistemas dinâmicos.

--- 







