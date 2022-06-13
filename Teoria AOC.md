# Respostas Teoricas AOC

- [Respostas Teoricas AOC](#respostas-teoricas-aoc)
  - [Classificacoes de computador](#classificacoes-de-computador)
    - [Abstração](#abstração)
    - [ISA](#isa)
    - [Sistema](#sistema)
    - [Memoria](#memoria)
    - [CPU](#cpu)
    - [Bit, byte e palavra](#bit-byte-e-palavra)
    - [Vazão e tempo de resposta](#vazão-e-tempo-de-resposta)
    - [Supercomputador, microcomputador, minicomputadores](#supercomputador-microcomputador-minicomputadores)
  - [computador inspirado em John von Neumann](#computador-inspirado-em-john-von-neumann)
  - [Aritimetica binária Lista 04](#aritimetica-binária-lista-04)
    - [Questão 2 - Passos de um programa em C](#questão-2---passos-de-um-programa-em-c)
      - [Resposta](#resposta)
    - [Questão 5 - ieee 754](#questão-5---ieee-754)
      - [Resposta](#resposta-1)
    - [Questão 7 - Demonstre a diferença](#questão-7---demonstre-a-diferença)
      - [Resposta](#resposta-2)
    - [Questão 8 - words x registradores](#questão-8---words-x-registradores)
      - [Resposta](#resposta-3)
  - [ISA MIPS - Lista 05](#isa-mips---lista-05)
    - [Questão 2 - CISC X RISC](#questão-2---cisc-x-risc)
      - [Resposta](#resposta-4)
    - [Questão 7 - Transcreva em português](#questão-7---transcreva-em-português)
      - [resposta](#resposta-5)
    - [Questão 8 - Fundamentos ISA](#questão-8---fundamentos-isa)
      - [resposta](#resposta-6)
  - [CPU Performance - Lista 06](#cpu-performance---lista-06)
    - [Questão 5 - Dois processadores de mesma isa](#questão-5---dois-processadores-de-mesma-isa)
      - [Resposta](#resposta-7)
    - [Questao 7 - escolha de variável](#questao-7---escolha-de-variável)
      - [Resposta](#resposta-8)
    - [Questão 8 - Explique como o compilador pode afetar no desempenho](#questão-8---explique-como-o-compilador-pode-afetar-no-desempenho)
      - [Resposta](#resposta-9)
    - [Questão 12 - performance](#questão-12---performance)
      - [Resposta](#resposta-10)
    - [Questão 14 - um cenário ideal](#questão-14---um-cenário-ideal)
      - [Resposta](#resposta-11)
    - [Questão 16 - variáveis que influenciam no desempenho](#questão-16---variáveis-que-influenciam-no-desempenho)
      - [Resposta](#resposta-12)
  - [Pipeline - Lista 07](#pipeline---lista-07)
    - [Questão 2. Arquitetura de von Neumann](#questão-2-arquitetura-de-von-neumann)
      - [Resposta](#resposta-13)
    - [Questão 3. Características Gerais do pipeline](#questão-3-características-gerais-do-pipeline)
      - [Resposta](#resposta-14)
    - [Questão 4. Visão geral do processo de execução](#questão-4-visão-geral-do-processo-de-execução)
      - [resposta](#resposta-15)
    - [extra - CPU monociclo, multicilo e Pipelined](#extra---cpu-monociclo-multicilo-e-pipelined)
    - [Hazards](#hazards)
  - [Memoria - Lista 08](#memoria---lista-08)
    - [Questao 6 - von Neumann](#questao-6---von-neumann)
      - [Resposta](#resposta-16)
    - [Questão 3 - Localidade](#questão-3---localidade)
      - [Resposta](#resposta-17)
    - [REM e RDM, BE, BD, BC](#rem-e-rdm-be-bd-bc)


## Classificacoes de computador

### Abstração
Abstraction is one of the four cornerstones of Computer Science. It involves filtering out – essentially, ignoring - the characteristics that we don't need in order to concentrate on those that we do.

### ISA
An Instruction Set Architecture (ISA) is part of the abstract model of a computer that defines how the CPU is controlled by the software. The ISA acts as an interface between the hardware and the software, specifying both what the processor is capable of doing as well as how it gets done.

The ISA provides the only way through which a user is able to interact with the hardware. It can be viewed as a programmer’s manual because it’s the portion of the machine that’s visible to the assembly language programmer, the compiler writer, and the application programmer.

The ISA defines the supported data types, the registers, how the hardware manages main memory, key features (such as virtual memory), which instructions a microprocessor can execute, and the input/output model of multiple ISA implementations. The ISA can be extended by adding instructions or other capabilities, or by adding support for larger addresses and data values.

### Sistema
Conjunto de partes coordenadas que concorrem para um determinado objetivo

### Memoria
Um subsistema do sistema de computação que armazena não só os programas a serem executados pela CPU, como também as informações introduzidas por algum componente de Entrada ou calculados ao decorrer da execução.

### CPU
Realiza as operações matemáticas com os dados e controla o que deve ser realizado pelos demais componentes

### Bit, byte e palavra
bit: Menor unidade de informação armazenavel, digito binario

Byte: Conjunto de 8 bits

Palavra: Unidade de transferência entre a CPU e a Memória

### Vazão e tempo de resposta
Vazão define a quantidade de transações que pode ser executada por um sistema na unidade de tempo. (quantas operações em paralelo num determinado instante).

Tempo de resposta é uma medida ligada ao desempenho do sistema como um todo, e define quanto tempo leva determinado componente a realizar determinada tarefa

### Supercomputador, microcomputador, minicomputadores
- supercomputador (mainframe): É projetado para executar grandes quantidades de cálculos matemáticos o mais rapidamente possível. Aplicação científica ou estratégica. Alto processamento, muita capacidade de memória, grande volume de dados. Custa muito elevado. 100-900 Mips (milhoes de instruççoes por segundo)

- microcomputador (desktop, laptop, notebook, celular): uso pessoal e CPU em um único chip, menor tamanho, menor capacidade de processamento

- minicomputadores: Máquinas projetadas para atender simultanemante a demanda por execução de programas de vários usuários. mais poderosos que microcomputadores, menos que supercomputadores, pequenas e medias empresas. 10-30 Mips

## computador inspirado em John von Neumann
Dados e instruções residem na mesma memória, dados e instruções sao acessados pelo seu endereço. A execução ocorre de forma sequencial.

___

## Aritimetica binária Lista 04

### Questão 2 - Passos de um programa em C

Descreva as quatro etapas para a transformação de um programa em C, armazenado em um arquivo no disco, para um programa executando em um computador. Explique o que ocorre em cada uma dessas etapas.

#### Resposta
Etapas:
- Converter Para Assembly
- Converter para ling. Binária
- link editor
- Loader

- O programa é primeiramente convertido para a linguagem Assembly através do compilador da linguagem especifica, neste caso o compilador da linguagem C.
- Este código em Assembly é então convertido para a linguagem binária pelo Assembler utilizando as especificações da ISA.
- Este código binário passa por um link editor, que ira relacionar todas as instruções, bibliotecas e objetos necessários para o funcionamento do código, gerando um arquivo executável.
- Com o arquivo executável gerado, a ultima etapa é o Loader, onde o sistema operacional lê o arquivo executável e o carrega na memória para executa-lo.


### Questão 5 - ieee 754

Represente (e demonstre o passo a passo)  o número  -0,5 na notação IEEE 754 de precisão simples

#### Resposta
A notação IEEE 754 é uma notação, normalmente de 32 bits, que serve para representar a seguinte formula
> (-1)^s * 1.mantissa*2^exp  
Em 32 bits, a sequencia dos bits é:
> o bit mais significativo é o bit de **s**, os próximos **8 bits** é reservado para o expoente com um bias de 127. e os restantes **23 bits** é a fração da normatização científica.
primeiro é preciso verificar o bit de sinal, que neste caso sera 1 ja que o numero é negativo.
em seguida devemos normalizar o valor (0,5) em binario no formato de 1,xyzw...*2^n, onde queremos encontrar n.
para 0,5 isso significa que teremos: 0,1 em binario que sera => 1,0*2^-1 normalizado
Apos isso devemos encontrar a característica, que calculamos somando o expoente n ao bias, considerando o bias de 127, teremos a característica de 126 para 1,0*2^-1
Apos isso devemos escrever a mantissa, que é os números xyzw... que seguem apos a virgula no valor normalizado, que neste caso é 0.
portanto, para montar o numero em IEEE 754 com bias de 127 teremos o seguinte formato:
sinal + (expoente + bias) + xyzw..... E portanto temos que -0.5 em IEEE 754 é:
1 01111110 00000000000000000000000 para 32 bits.



### Questão 7 - Demonstre a diferença
Seja duas variáves  X e Y.  X é do tipo char e armazena a informação '2'.  Y é do tipo unsigned int e armazena a informação 2. 

Pergunta:  X == Y ? (X é igual a Y)? Demonstre sua resposta. (basei seus argumentos na forma com os os dados são representados - considere que o computador em seja de 8 bits)

#### Resposta
X não e igual a Y, apesar da representação simbólica ser igual para nos humanos (o numero 2) o que acontece é que ao informar o computador que x é um char, o mesmo ira utilizar uma representação de carácter, como a representação ASCII, enquanto a variável Y usara uma representação numérica, ou simplesmente armazenar o numero em binário, de tal forma teremos que:
x armazenara o valor: 00110010
enquanto y armazenara o valor: 00000010
e portanto, x nao é igual a y.


### Questão 8 - words x registradores
O que entende-se por tamanho da word de um processador? Que relação o tamanho da word tem com os registradores?

#### Resposta
tamanho da word de um processador é, em outras palavras, o tamanho dos dados processados pela CPU. 
Os registradores da CPU irão receber instruções e enviar dados utilizando este comprimento de palavra, porquanto, a word de um processador interfere em todo o funcionamento do mesmo, já que ele funcionara em torno do tamanho da palavra. 

___

## ISA MIPS - Lista 05 

### Questão 2 - CISC X RISC

> Este exercício foi extraído do cap1 da 3a. edicao do Patteron e Hennessy, nele você avaliará a diferença de desempenho entre duas arquiteturas de CPU, a CISC (Complex Instruction Set Computing) e a RISC (Reduced Instruction Set Computing).
Genericamente falando, as CPUs CISC possuem instruções mais complexas do que as CPUs RISC e, portanto, precisam de menos instruções para realizar as mesmas tarefas. Entretanto, em geral uma instrução CISC, por ser mais complexa, leva mais tempo para ser completada do que uma instrução RISC. Considere que uma determinada tarefa precise de P instruções CISC e 2P instruções RISC, e que uma instrução CISC leva 8T ns (nanossegundos) para ser completada enquanto uma instrução RISC leva 2T ns. Com essas considerações, qual arquitetura apresenta o melhor desempenho? (Apresente também os cálculos e suas considerações)

#### Resposta

Na maquina CISC temos que a execução da tarefa precisa de P instruções de 8Tns cada, totalizando 8T ns
na maquina RISC temos que a execução da mesma tarefa é feita em 2P instruções de 2Tns cada, totalizando 4T ns.
Podemos afirmar, portanto, que para esse conjunto de tarefas, a arquitetura RISC possui maior desempenho.

### Questão 7 - Transcreva em português

Transcreva em português, claro e inequívoco, o resultado de cada uma das instruções do MIPS

#### resposta
- a) `lw $t6, 400($s5)`
armazene no registrador $t6 a word (conteúdo de 4byte) encontrado no endereço $s5+400 da MP 

- b) `sw $t6, 400($s5)`
armazene no endereço $s5+400 da MP a word (conteúdo de 4byte) do registrador $t6 

- c) `slt $t6, $s4, 10`
registra em booleano (verdadeiro ou falso) o resultado da operação $s1<10 (verdadeiro se $s1 for menor que 10 e falso se for maior ou igual a 10) 

- d) `beq $t5,$zero, Label_X`
se $t5 for igual a $zero, passe a executar as instruções do bloco "Label_X"


### Questão 8 - Fundamentos ISA

Sobre os conceitos fundamentais de ISA (Instruction Set Architecture), analise as proposições e marque aquela(s) verdadeira(s):

#### resposta

- Registradores, Instruções, Formas de Endereçamento e Tamanho da Word constituem os elementos mais relevantes de uma ISA
- É uma característica importante para a diferenciação entre RISC e CISC
- Um código em Assembly acessa diretamente a ISA, por isso é dito que a ISA é uma interface para o programador de baixo nível.
- É uma abstração que cria uma interface de acesso direto às funcionalidades da CPU


___

## CPU Performance - Lista 06

### Questão 5 - Dois processadores de mesma isa

Considere dois processadores de mesma ISA, um de 2GHZ e outro de 3GHZ.

a) Posso afirmar que o segundo, de 3GHZ é mais rápido que o primeiro?

b) Justifique sua resposta  com cálculos e as considerações relevantes. 

#### Resposta
a) não

b) A frequência de uma CPU não é o único fator determinate do tempo de execução de um determinado programa, considerando que o mesmo programa seja usado, o outro fator determinante para o cálculo do tempo é a quantidade de ciclos por instrução, conhecida como CPI, conforme vemos na formula abaixo:
> t = (Instruções*CPI)/Frequência
é possível perceber que o tempo de execução é inversamente proporcional a frequência (quanto maior a frequência, menor o tempo) e diretamente proporcional a CPI (quanto maior a CPI, maior o tempo), desta forma, se o processador de 3GHZ tiver uma CPI maior que 0.67 da CPI do processador de 2GHZ, o mesmo demorara mais para executar os mesmos programas do processador de 2GHz


### Questao 7 - escolha de variável
Explique como  a escolha de uma variável (float ou int por exemplo) pode afetar o desempenho de uma CPU.

#### Resposta
Uma cadeia do tipo Int pode ser armazenada na memória de forma mais simples, sendo facilmente processada e interpretada, já um numero float requer um processamento maior para que seja interpretado e armazenado, requerendo mais etapas relativo ao tipo int.


### Questão 8 - Explique como o compilador pode afetar no desempenho
Explique como o compilador pode afetar no desempenho de uma cpu.

#### Resposta
O compilador afeta o desempenho de uma CPU ao escolher as instruções da ISA, podendo trocar algumas instruções do código por outras mais rápidas (como trocar operações de multiplicar por bases de 2 por sll) e ao reorganizar a ordem das instruções para diminuir os Hazards do pipeline.


### Questão 12 - performance
Sobre análise de desemepenho de processadores assinale a(s) alternativa(s) correta(s)

#### Resposta
- O tempo de execução de CPU é também chamado tempo de CPU que significa o tempo real que a CPU gasta calculando para uma tarefa específica.

- Throughput Also called bandwidth. A measure of performance, it is the number of tasks completed per unit time.
- Tempo de resposta é uma medida de desempenho, ele indica o tempo necessário para que várias tarefas sejam completadas por unidade de tempo.
- Um bom desempenho pode indicar alta vazão ou baixo tempo de resposta.


### Questão 14 - um cenário ideal
Um modelo ideal de processador seria uma máquina operando em alta frequência e baixo CPI, mas, na prática, isso é um objetivo não muito trivial de ser alcançado. Por quê?


#### Resposta
Porque a frequência de um processador determina o tempo que instrução é processada por ciclo da CPU, e existe um limite físico ditado pelo funcionamento do hardware do quanto tempo demora para uma instrução ser concluída, como o tempo de realizar cálculos, acessar a memória, verificação lógica etc. portanto, podemos concluir que ao aumentar a frequência (diminuir o tempo de ciclo da CPU) existe uma tendência natural de aumentar a quantidade de ciclos necessárias para completar uma instrução, para que a mesma fique o tempo necessário na CPU para ser concluída.


### Questão 16 - variáveis que influenciam no desempenho
Dos elementos abaixo descritos, assinale aquele(s) que tem(êm) influência sobre o desempenho de uma CPU 

#### Resposta
- Compilador
  
- Sistema Operacional
- Algoritmo
- Barramentos e E/S
- Duração do ciclo de clock
- Velocidade (frequência) do clock
- CPI 


___

## Pipeline - Lista 07

### Questão 2. Arquitetura de von Neumann
A Arquitetura de von Neumann estabelece um modelo de computador que possui uma CPU e uma memória principal (MP). Nesta MP residem dados e instruções. A CPU lê e escreve nessa MP e comunicação entre eles se dá via barramento. Essa arquitetura impacta o projeto do pipeline MIPS que pode apresentar um tipo específico de hazard.  

a) Qual é este tipo de hazard?

b) Como essa arquitetura tem tal impacto?

#### Resposta
a) Hazard Estrutural

b) O acesso a memória principal é feito através de um barramento com um limite físico de transferência de dados, portanto, caso duas ou mais instruções precisem acessar a mesma memória no mesmo tempo, um stall sera criado pois não há a capacidade física de atender todas as instruções simultaneamente.


### Questão 3. Características Gerais do pipeline
Sobre a técnica de pipeline, analise cada umas das proposições e assinale a(s) correta(s)

#### Resposta
- O Pipeline é uma técnica de melhoria de desempenho de processadores. Ela pode ser adotada em cpu's **multiciclo**. A ideia geral do pipeline e aproveitar os estágios de execução de uma instrução e executar num mesmo ciclo de clock várias instruções.

- A melhoria do pipeline **NÃO** se dá pela redução do tempo necessário para executar uma instrução, e sim por **aumentar a vazão**. Uma instrução numa máquina de 20 estágios de pipeline, seria em tese, 20 vezes mais rápida do que a de um processador sequencial (sem pipeline).

- Hazards são situações que vão impedir que todos os estágios do pipeline sejam preenchidos com alguma instrução. Eles representam perda de performance do pipeline, e o tratamento inadequado deles pode levar a cpu obter resultados incorretos no processamento de suas instruções. 

- O compilador poderá alterar a ordem das instruções, mantendo sua correção, para que as instruções que possuam dependência de dados se mantenham a uma determinada distância para evitar um hazard de **dados** no pipeline.

- Pipeline é uma técnica que explora o paralelismo entre as instruções em um fluxo de instruções sequenciais. Ela tem a vantagem substancial de que, diferente de programar um multiprocessador, ela é fundamentalmente invisível ao programador.

- Embora o compilador geralmente conte com o hardware para resolver dependências de hazard e garantir a execução correta, o compilador precisa compreender o pipeline a fim de alcançar o melhor desempenho. Caso contrário, stalls inesperados reduzirão o desempenho do código compilado. 


### Questão 4. Visão geral do processo de execução
Sobre o processo de execução assinale a(s) alternativa(s) CORRETA(S)

#### resposta
- Muito do que precisa ser feito para implementar as instruções no hardware, independente da classe exata da instrução, pode ser resumido a: 1o. **Receber** do programa (PC) à memória que contém o código e buscar a instrução dessa memória; 2o. Ler um ou mais registradores, usando campos da instrução para selecionar os registradores a serem lidos. Para a instrução load word, precisamos ler **dois** registradores. *A maioria das outras instruções exige a leitura de **tres** registradores.*

- Para executar qualquer instrução, precisamos começar buscando a instrução na memória. A fim de preparar para executar a próxima instrução, também temos de incrementar o contador de programa de modo que aponte para a próxima instrução, 4 bytes depois (no caso de uma palavras de 32bits). 

- No MIPS, as instruções de formato R, todas elas, lêem dois registradores, realizam uma operação na ALU com o conteúdo dos registradores e escrevem o resultado em um registrador. Chamamos essas instruções de instruções tipo R ou instruções lógicas ou aritméticas (já que elas realizam operações lógicas ou aritméticas). Essa classe de instrução inclui add , sub , AND , OR e slt.  


### extra - CPU monociclo, multicilo e Pipelined
MonoCiclo: Toda instrução demora um longo ciclo para ser executada;

MultiCiclo: As instruções passam apenas pelas etapas que precisam

Pipeline: uma cpu multiciclo onde cada ciclo da cpu conclui uma etapa diferente para cada instrução paralelamente presente nela.

### Hazards
Situações que diminuem a produtividade do Pipeline, ao impedir que uma instrução seja concluida em um determinado ciclo de clock, diminuindo momentaneamente a vasão do processador. São classificadas em:
- Hazard de Controle: acontece quando o pipeline assume o bloco de decisão errada em ao encontrar um bloco de controle (if, switch etc), fazendo com que as intruções que estavam na pipeline tenham que ser descartadas para que as corretas sejam processadas

- Hazard de Dados: Ocorre quando uma instrução necessitada de um dado que ainda esta sendo processado no pipeline. forwarding pode diminuir a penalização deste tipo de hazard

- Hazard Estrutural: Ocorre quando duas ou mais instruções na pipeline requerem o mesmo recurso, como duas instruções tentando acessar a memória simultaneamente.

___

## Memoria - Lista 08

### Questao 6 - von Neumann

> O ideal seria ter uma capacidade de memória infinitamente grande a ponto de qualquer palavra específica ... estar imediatamente disponível. ... Somos ... forçados a reconhecer a possibilidade de construir uma hierarquia de memórias, cada uma com capacidade maior do que a anterior, mas com acessibilidade menos rápida.
>> A. W. Burks, H. H. Goldstine e J. von Neumann 
>>>Preliminary Discussion of the Logical Design of an Electronic Computing Instrument, 1946

Esta afirmação de Burks, Goldstine e von Neumann, lá na década de 1946 já apontava uma questão que é atual ainda nos dias de hoje. Faça seus comentários.

#### Resposta

Em um mundo ideal, teríamos uma única memória capaz de armazenar e escrever de forma permanente todos os dados, instruções e arquivos necessários e capaz de fazer a transferência desses dados para o processador de forma eficiente, sem demoras ou perdas (na mesma velocidade de um ciclo de clock).

Porém, atualmente, um dos gargalos para a performance de um computador é justamente a sua memória, seja a capacidade da mesma, ou a velocidade para escrever/ler dados. Podemos imaginar que a escolha de uma memória e feita com as seguintes combinações:
- Capacidade Alta, Custo Alto, Velocidade Baixa
  
- Capacidade Baixa, Custo Alto, Velocidade Alta
  
De tal forma que, quanto mais rápido querermos fazer uma memória ser, menor a sua capacidade e maior o seu custo, chegando a inviabilizar um projeto. Porém, se simplesmente optarmos por uma única memória com grande capacidade e custo baixo, teríamos uma grande perda de performance, ao ponto de inviabilizar um projeto.

Portanto, como uma forma de resolver tal problema, trabalhamos com vários tipos diferentes de memória, utilizando de hierarquia e algoritmos de comunicação ente as mesmas para que possamos ter a melhor performance com um custo razoável. Armazenando instruções e dados que desejamos reproduzir regularmente em memórias não voláteis de alta capacidade, custo baixo e velocidade baixa, e armazenamos as instruções e dados requeridos instantaneamente, ou em um futuro muito próximo, em memórias voláteis de baixa capacidade, alto custo e velocidade alta.

É comum que um sistema computacional possua um subsistema de memória com diferentes tipos de memórias que estão continuamente transferindo dados entre si, um exemplo genérico para um computador pessoal (desktop) seria:
    Disco rígido (não volátil, capacidade alta, custo baixo, velocidade baixa): Armazena os programas, arquivos e sistema operacional 
    Memoria principal (volátil, capacidade média, custo médio, velocidade média): Armazena parte dos arquivos dos programas, sistema operacional e dados que estão sendo utilizados no momento.
    Cache do processador (volátil, capacidade baixa, custo alto, velocidade alta): Armazena parte das linhas de instruções dos programas (e do sistema operacional) que estão sendo/serão nos próximos instantes de segundos pela CPU.
    Registradores (volátil, capacidade muito baixa, custo muito alto, velocidade muito alta): Armazena as linhas de códigos que estão sendo/serão processadas nas próximas instruções pela CPU.

Portanto, é possível concluir que o problema e a solução teorizados em 1946 por Burks, Goldstine e Neumann existe e são relevantes atualmente, de tal forma que descreve o nosso cenário atual de hierarquia de memória.

### Questão 3 - Localidade 
Explique como os princípios da localidade temporal e espacial são explorados para manter o sistema hierárquico de memória.

#### Resposta

Atualmente é comum termos computadores pessoais (desktops) com disco rigido de Terabytes, memória principal de Gigabytes e caches de megabytes e kilobyte. Porém, O tempo de acesso a memoria secundária e principal é muito alto, fazendo com que a CPU tenha pausar suas instruções esperando o tempo necessário para acessar estas memórias. Como o tempo de acesso a memória cache é muito próximo ao ciclo de clock da CPU, o tempo de acesso é muitas vezes menor, fazendo com que, para termos uma alta performance da CPU, necessitamos que mais de 90% dos dados acessados pela CPU encontrem-se na memória Cache. O que a princípio parece ser impossível, como fazer "caber" Gigabytes em kilobytes? Como reproduzir um programa de gigabytes de dados na capacidade de kilobyte da memória cache?
Pesquisas e amostragens sobre como os programas sao, em geral, escritos e executados pela CPU chegaram a conclusão que a execução de programas se realiza em pequenos grupos de instruções que estão em endereços próximos uns aos outros e que, em média, se repetem. Destas pesquisas, temos os Princípios da localidade espacial e temporal.

Localidade Espacial: Se um programa acessa uma palavra na memória, há uma boa probabilidade de que ele em breve acesse em sequencia uma palavra subsequente, ou um endereço adjacente aquela palavra.
Localidade Temporal: Se um programa acessa uma palavra na memória, há uma boa probabilidade de que ele acessa a mesma palavra novamente.

Utilizando estes dois princípios, é possivel escolher os pequenos grupos de instruções que possuem grande probabilidade de serem requisitados pela CPU. Desta forma, pequenos grupos de instruções dos programas de Gigabytes podem ser processados utilizando, em cerca de mais de 90% do tempo, o acesso ao cache ao invés da memoria principal ou secundária.

### REM e RDM, BE, BD, BC
- REM: Registrador de endereço da memoria: Armazena temporariamente o endereço de acesso a uma posicao de memória ao se iniciar uma operacao de leitura ou escrita

- RDM: Registrador de Dados da memoria: Armazena temporariamente uma informação que esteja sendo transferida da memória para a CPU
- BE: Barramento de Endereço: Interliga a CPU a memoria de forma uniderecional, transfere os bits que significam um endereço
- BD: Barramento de Dados: Interliga a CPU a memoria de forma bidirecional, transfere os dados contidos no endereço de memoria nas operações de write/read
- BC: Barramento de Controle: Interliga a CPU a memoria de forma bidirecional, a CPU manda o sinal de leitura/escrita, a memoria manda sinal de wait