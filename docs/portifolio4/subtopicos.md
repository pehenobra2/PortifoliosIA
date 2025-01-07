# Agentes Baseados em Conhecimento

Os **agentes baseados em conhecimento** utilizam uma **base de conhecimento (KB)** para tomar decisões e executar ações de forma inteligente. A KB é composta por sentenças, expressas em uma linguagem específica para representação de conhecimento, que descrevem informações sobre o mundo. Essas sentenças podem ser adicionadas ou consultadas por meio das operações **TELL** (informar) e **ASK** (perguntar).

O funcionamento básico envolve três etapas principais: o agente percebe o ambiente, atualiza sua base de conhecimento com as percepções e consulta a KB para decidir a melhor ação a ser executada. Após realizar a ação, ele registra na KB que a ação foi concluída. Esse processo contínuo permite que o agente raciocine sobre o estado do mundo e atinja suas metas de forma adaptativa.

Diferentemente dos agentes puramente procedurais, os agentes baseados em conhecimento adotam uma abordagem **declarativa**, onde as regras e fatos são definidos independentemente do código, facilitando a compreensão e a manutenção do comportamento do agente. Além disso, esses agentes podem combinar elementos declarativos e procedurais, e até aprender novos conhecimentos a partir de suas interações com o ambiente.

Esse modelo exemplifica como um agente pode tomar decisões inteligentes, raciocinando sobre seu conhecimento para atingir objetivos, como em aplicações práticas de veículos autônomos ou assistentes virtuais.

## Wumpus World

O **Wumpus World** é um ambiente desafiador onde o agente deve explorar uma caverna composta por salas conectadas. O objetivo é encontrar o **ouro** e escapar da caverna, evitando perigos como o **wumpus**, que pode devorar o agente, e os **poços**, que podem fazer o agente cair.

O ambiente é uma **malha 4x4 de salas**, com o agente começando em [1,1]. Ele pode realizar ações como mover-se, atirar uma flecha para derrotar o wumpus, pegar o ouro ou sair da caverna. O agente também possui sensores que percebem **fedor**, **brisa**, **brilho**, **impacto** e **grito**.

No **Wumpus World**, o agente começa com conhecimento limitado, como saber que está na posição [1,1] e que essa sala é segura. À medida que explora, ele coleta percepções que ajudam a atualizar sua base de conhecimento e tomar decisões, como a presença de **fedor** (indicando a proximidade do wumpus) ou de **brisa** (indicando a proximidade de um poço).

A tarefa do agente é usar **raciocínio lógico** para superar sua ignorância inicial sobre o ambiente e deduzir a localização do wumpus e dos poços. A partir dessas deduções, o agente decide explorar mais ou tentar pegar o ouro e sair da caverna com segurança.

Esse processo contínuo de raciocínio lógico, aliado à atualização constante do conhecimento, é fundamental para o sucesso do agente no **Wumpus World**.

# Lógica

A **lógica** estuda os princípios do raciocínio válido e da inferência, sendo utilizada na inteligência artificial para representar conhecimento e deduzir conclusões. As sentenças lógicas podem ser **verdadeiras** ou **falsas**, e sua validade é regida por dois componentes principais: **sintaxe** e **semântica**.

## Sintaxe

A sintaxe define as regras que determinam a estrutura válida das sentenças em um sistema lógico, especificando como os símbolos devem ser combinados para formar expressões bem formadas. Por exemplo, em aritmética, a expressão "x + y = 4" é válida, enquanto "x4y+ =" não é, pois não segue as regras de formação.

## Semântica

A semântica refere-se ao significado das sentenças, ou seja, à sua **verdade** em relação a diferentes **modelos** ou **mundos possíveis**. A semântica define quando uma sentença é verdadeira ou falsa em um dado contexto. Por exemplo, a sentença "x + y = 4" é verdadeira em um mundo onde x = 2 e y = 2, mas falsa em um mundo onde x = 1 e y = 1.

## Consequência Lógica e Raciocínio

A **consequência lógica** (α |= β) indica que, se α é verdadeira, então β também deve ser verdadeira. Essa relação é fundamental para o **raciocínio lógico**, que permite deduzir novas sentenças a partir de premissas conhecidas.

Algoritmos de inferência podem ser **corretos** (preservando a verdade) e **completos** (capazes de derivar todas as consequências lógicas). Embora a verificação de modelos seja uma ferramenta poderosa, ela pode ser computacionalmente cara.

## Aplicações em Agentes Autônomos

Em agentes autônomos, como no **Wumpus World**, a lógica permite que o agente combine percepções e conhecimento para tomar decisões racionais. O agente utiliza seu conhecimento sobre o ambiente, como regras sobre a presença do wumpus ou dos poços, para deduzir ações seguras e alcançar seus objetivos de forma adaptativa.

# Processo de Inferência

O **processo de inferência** em lógica proposicional visa derivar conclusões válidas a partir de premissas conhecidas. Uma abordagem simples é a **enumeração de modelos**, onde verificamos se uma sentença α é consequência lógica de uma base de conhecimento BC, examinando todos os possíveis modelos (ou atribuições de valores de verdadeiro e falso para as proposições). A verificação de consequência lógica pode ser feita por meio de algoritmos como **CONSEQUÊNCIA-LÓGICA-TV?**, que explora um espaço finito de atribuições de valores, retornando verdadeiro ou falso dependendo de se a sentença α é verdadeira em todos os modelos onde BC é verdadeira.

Embora esse algoritmo seja **consistente** e **completo**, sua **complexidade de tempo** é exponencial, O(2^n), onde n é o número de proposições. Isso ocorre porque há 2^n modelos possíveis, e o algoritmo precisa examinar todos. A complexidade de espaço é O(n), devido à busca em profundidade, mas o tempo de execução pode ser proibitivo para bases de conhecimento grandes.

Uma alternativa à enumeração de modelos é o uso de **regras de inferência**. Regras como **Modus Ponens** e **Eliminação do E** são fundamentais para derivar conclusões diretamente de premissas. Modus Ponens, por exemplo, permite deduzir β a partir de α ⇒ β e α. Além disso, equivalências lógicas como **eliminação de bicondicional** e **contraposição** podem simplificar o processo de dedução.

Em sistemas eficientes, como no **Wumpus World**, as **provas automáticas** podem ser realizadas aplicando essas regras de inferência para deduzir sentenças a partir das percepções e do conhecimento do ambiente. Embora o algoritmo de busca de provas seja mais eficiente que a enumeração de modelos, ele ainda enfrenta o desafio da **explosão combinatória**, onde o número de possibilidades aumenta rapidamente.

Uma característica importante dos sistemas lógicos é a **monotonicidade**, que garante que a adição de novas informações à base de conhecimento não invalida conclusões previamente tiradas. Isso significa que o conjunto de consequências lógicas só pode crescer à medida que novas informações são acrescentadas, mantendo a consistência do sistema lógico.

Portanto, o processo de inferência envolve a combinação de técnicas como **enumeração de modelos** e **regras de inferência**, com o objetivo de derivar conclusões válidas a partir de uma base de conhecimento. No entanto, devido à sua complexidade, o uso de algoritmos mais eficientes é essencial para lidar com bases de conhecimento grandes e complexas.

# Agentes Baseados em Lógica Proposicional

Agentes baseados em lógica proposicional utilizam a lógica proposicional para representar e inferir o conhecimento sobre o ambiente. No contexto do **Wumpus World**, esses agentes deduzem o estado atual do ambiente, como onde estão e quais quadrados são seguros ou perigosos, com base nas percepções adquiridas.

## Funcionamento do Agente

O agente opera a partir de uma base de conhecimento (BC), composta por axiomas e sentenças de percepção. Os axiomas representam o conhecimento atemporal sobre o mundo, como a ausência de um poço ou do Wumpus no quadrado inicial. As sentenças de percepção são adicionadas à BC conforme o agente faz novas percepções sobre o ambiente, como a presença de fedor, brisa ou brilho em um quadrado.

Usando a inferência lógica, o agente deduz o estado atual do mundo. Por exemplo, ao perceber uma brisa, o agente sabe que um dos quadrados vizinhos contém um poço, o que ajuda a determinar quadrados seguros ou perigosos. O agente realiza essas deduções continuamente, ajustando seu comportamento conforme novas percepções são recebidas.

Além disso, o agente deve tomar decisões sobre quais ações executar com base nas percepções e no estado deduzido, formando um plano de ação que pode incluir explorar novos quadrados ou tentar pegar o Wumpus. A inferência lógica orienta o agente na escolha de ações mais seguras.

## Estimação de Estado

Um dos desafios dos agentes baseados em lógica proposicional é o aumento do custo computacional à medida que o número de percepções cresce. Para lidar com isso, o agente pode usar a técnica de **estimação de estado**, que atualiza continuamente o estado de crença do agente sem refazer todas as deduções. Uma representação aproximada, como a **forma normal conjuntiva (1-FNC)**, pode ser utilizada para manter um estado de crença eficiente, garantindo a operação prática em ambientes dinâmicos.

Embora a lógica proposicional seja poderosa na representação e dedução do conhecimento, o custo computacional pode aumentar exponencialmente. Técnicas como estimação de estado e representações compactas do conhecimento são cruciais para garantir a eficiência do agente no **Wumpus World**.
