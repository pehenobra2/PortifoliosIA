# Agentes Baseados em Conhecimento

Os **agentes baseados em conhecimento** utilizam uma **base de conhecimento (KB)** para tomar decisões e executar ações de forma inteligente. A KB é composta por sentenças, expressas em uma linguagem específica para representação de conhecimento, que descrevem informações sobre o mundo. Essas sentenças podem ser adicionadas ou consultadas por meio de operações chamadas **TELL** (informar) e **ASK** (perguntar).

O funcionamento básico envolve três etapas principais: o agente percebe o ambiente, atualiza sua base de conhecimento com as percepções e consulta a KB para decidir a melhor ação a ser executada. Após realizar a ação, ele registra na KB que a ação foi concluída. Esse processo é contínuo e permite que o agente raciocine sobre o estado do mundo e alcance suas metas de maneira adaptável.

Diferentemente de agentes puramente procedurais, os agentes baseados em conhecimento utilizam uma abordagem **declarativa**, permitindo que as regras e fatos sejam definidos independentemente do código. Isso facilita a compreensão e manutenção do comportamento do agente. Além disso, eles podem combinar elementos declarativos e procedurais, e até mesmo aprender novos conhecimentos a partir de suas interações com o ambiente.

Esse modelo exemplifica como um agente pode tomar decisões inteligentes, raciocinando sobre seu conhecimento para atingir objetivos, como mostrado em aplicações práticas, como veículos autônomos ou assistentes virtuais.

## Wumpus World

O **wumpus world** é um ambiente desafiador no qual o agente deve explorar uma caverna composta por salas conectadas. O objetivo é encontrar o **ouro** e escapar da caverna, evitando perigos como o **wumpus**, que pode devorar o agente, e os **poços**, que podem fazer o agente cair.

O ambiente é uma **malha 4x4 de salas**, com o agente começando em [1,1]. Ele pode realizar ações como mover-se, atirar uma flecha para derrotar o wumpus, pegar o ouro ou escalar para sair da caverna. O agente também possui sensores que percebem **fedor**, **brisa**, **brilho**, **impacto** e **grito**.

No **Wumpus World**, o agente começa com um conhecimento limitado sobre o ambiente, como saber que está na posição [1,1] e que essa sala é segura. À medida que explora, ele coleta percepções que ajudam a atualizar sua base de conhecimento e tomar decisões seguras, como a presença de um **fedor** (indicando a proximidade do wumpus) ou de uma **brisa** (indicando um poço).

A tarefa do agente é usar **raciocínio lógico** para superar sua ignorância inicial sobre o ambiente, como a localização do wumpus e dos poços. A partir das percepções e deduções, o agente decide entre explorar mais ou tentar pegar o ouro e sair da caverna com segurança.

Esse processo de raciocínio lógico, aliado à atualização constante do conhecimento, é fundamental para o sucesso do agente no **Wumpus World**.

# Lógica

A **lógica** estuda os princípios do raciocínio válido e da inferência. Em inteligência artificial, ela é usada para representar conhecimento e deduzir conclusões. As sentenças lógicas podem ser **verdadeiras** ou **falsas**, e sua validade é regida por dois componentes principais: **sintaxe** e **semântica**.

## Sintaxe

A sintaxe define as regras que determinam a estrutura válida das sentenças em um sistema lógico. Ou seja, especifica como os símbolos devem ser combinados para formar expressões bem formadas. Por exemplo, em aritmética, a expressão "x + y = 4" é válida, enquanto "x4y+ =" não é, pois não segue as regras de formação.

## Semântica

A semântica refere-se ao significado das sentenças, ou seja, à sua **verdade** em relação a diferentes **modelos** ou **mundos possíveis**. A semântica define quando uma sentença é verdadeira ou falsa em um dado contexto. Por exemplo, a sentença "x + y = 4" é verdadeira em um mundo onde x = 2 e y = 2, mas falsa em um mundo onde x = 1 e y = 1.

## Consequência Lógica e Raciocínio

A **consequência lógica** (α |= β) indica que, se α é verdadeira, então β também deve ser verdadeira. Essa relação é fundamental para o **raciocínio lógico**, que permite deduzir novas sentenças a partir de premissas conhecidas.

Os algoritmos de inferência podem ser **corretos** (preservando a verdade) e **completos** (capazes de derivar todas as consequências lógicas). Embora a verificação de modelos seja uma ferramenta poderosa, ela pode ser computacionalmente cara.

## Aplicações em Agentes Autônomos

Em agentes autônomos, como no **mundo de Wumpus**, a lógica permite que o agente combine percepções e conhecimento para tomar decisões racionais. O agente utiliza seu conhecimento sobre o ambiente, como regras sobre a presença do wumpus ou dos poços, para deduzir ações seguras e alcançar seus objetivos de forma adaptativa.

# Processo de inferência
# Agente baseado em lógica proposicional

# Referências
