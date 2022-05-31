# Estrutura de Dados I

- [Estrutura de Dados I](#estrutura-de-dados-i)
  - [Conceitos bases](#conceitos-bases)
    - [Vetores](#vetores)
      - [Passagem de vetores para funções](#passagem-de-vetores-para-funções)
    - [Alocação dinâmica](#alocação-dinâmica)
    - [Tipos de dados Básicos](#tipos-de-dados-básicos)
    - [O tipo Estrutura](#o-tipo-estrutura)
      - [Passagem de estruturas para funções](#passagem-de-estruturas-para-funções)
      - [Alocação dinâmica de Struct](#alocação-dinâmica-de-struct)
    - [Typedef](#typedef)
    - [Tipo união](#tipo-união)
    - [Tipo enumeração](#tipo-enumeração)
  - [Tipos de dados](#tipos-de-dados)
  - [Listas Simples](#listas-simples)
  - [Lista Encadeada](#lista-encadeada)
    - [Função de inicialização](#função-de-inicialização)
    - [Função de inserção](#função-de-inserção)
    - [Funcao que percorre os elementos da lista](#funcao-que-percorre-os-elementos-da-lista)
    - [Funcao que verifica se a lista esta vazia](#funcao-que-verifica-se-a-lista-esta-vazia)
    - [Funcao de Busca](#funcao-de-busca)
    - [Função que retira um elemento da lista](#função-que-retira-um-elemento-da-lista)
    - [Funcao para librar a lista](#funcao-para-librar-a-lista)
    - [Inserir no meio](#inserir-no-meio)
  - [Listas circulares](#listas-circulares)
  - [Listas duplamente encadeadas](#listas-duplamente-encadeadas)
    - [Funcao de insercao](#funcao-de-insercao)
    - [Funcao de busca](#funcao-de-busca-1)
    - [Funcao que retira um elemento](#funcao-que-retira-um-elemento)
  - [Lista circular duplamente encadeada](#lista-circular-duplamente-encadeada)
  - [Pilhas](#pilhas)
    - [Pilhas com vetor](#pilhas-com-vetor)
    - [Pilha com lista](#pilha-com-lista)
  - [Filas](#filas)
    - [Filas com Vetor](#filas-com-vetor)
    - [filas com lista](#filas-com-lista)
  - [Deque (fila dupla)](#deque-fila-dupla)
    - [Deque (fila dupla) com vetor](#deque-fila-dupla-com-vetor)
    - [Deque (fila dupla) com lista](#deque-fila-dupla-com-lista)

## Conceitos bases

### Vetores
```c
int v[10]
scanf("%f", &v[i]);
```

- É reservado um espaço de memória **continuo**
- O acesso a cada elemento é feito através de uma _indexação da variável v_
  - (no exemplo) os items estao indexados de v[0] à v[9]
    - v[10]: invasão de memória
- passamos para a função scanf o endereço de cada elemento do vetor ( &v[i]), pois desejamos que os valores capturados sejam armazenados nos elementos do vetor.
- Existe uma forte associalção entre **vetores e ponteiros**
  - a variável _v_ armazena o **ENDERECO INICIAL** do vetor
    - v aponta para o primeiro elemento do vetor.

> Aritimética de ponteiros
v+0 -> aponta para o primeiro elemento do vetor
v+2 -> aponta para o terceiro elemento do vetor
v+9 -> aponta para o último elemento do vetor

escrever &v[i] é equivalente a escrever (v+i). De maneira análoga, escrever v[i] é equivalente a escrever *(v+i)

#### Passagem de vetores para funções
consiste em: passar o endereço da primeira posição do vetor para um elemento de pointeiro da função.


### Alocação dinâmica
Precisamos informar ao compilador o número máximo de elementos, caso contrário, ele nao saberia o tamanho do espaço a ser reservado, _porém_, podemos requisitar ao sistema, no tempo de execução, um espaço de um determinado tamanho.
Este espaço alocado dinamicamente permanece reservado até que seja explicitamente liberado pelo programa. Se liberado, o espaço estara disponibilizado para outros usos.

```c
int *v
v = (int *) malloc(10*sizeof(int)); //reserva na memoria 10 espaços continuos que irao receber valores do tipo int
// caso não tenha espaço o suficiente na memoria, malloc ira retornar um endereço nulo (NULL)
if (v==NULL){
  printf("memoria insuficiente");
  exit(1);
}
//some code
free(v); //libera o espaco de memoria que foi alocado à v
```

### Tipos de dados Básicos
- char, int, float e seus respectivos ponteiros.

Para estruturar dados complexos, nos quais as informações são compostas por diversos campos, necessitamos de mecanismos que nos permitam agrupar tipos distintos.

### O tipo Estrutura
Em C podemos definir um tipo de dado cujos campos são compostos de vários valores de tipos mais simples, denomeado de **Struct**

~~~c
struct ponto {
float x;
float y;
};

int main (void)
{
struct ponto p;
printf("Digite as coordenadas do ponto(x y): ");
scanf("%f %f", &p.x, &p.y);
printf("O ponto fornecido foi: (%.2f,%.2f)\n", p.x, p.y);
return 0;
}

//struct para ponteiros
struct ponto *pp;
//acesso dos dados com ponteiro para struct
pp->x = 12;
~~~

#### Passagem de estruturas para funções

Pode ser feita de forma analoga à passagem de variáveis simples:
```c
void imprime (struct ponto p){
  printf("O ponto fornecido foi: (%.2f,%.2f)\n", p.x, p.y);
}
```
- Faz a cópia de toda a estrutura para a pilha e a função acessa os dados desta cópia
  - A função nao tem como alterar os valores dos elementos da estutura original.
  - Baixa eficiência

Passagem por ponteiro da Struct:
```c
void imprime (struct ponto* pp){
printf("O ponto fornecido foi: (%.2f,%.2f)\n", pp->x, pp->y);
}
```
  - Mais conveniente (passa apenas um ponteiro para a pilha ao invés da Struct inteira)
    - ponteiro ocupa 4 bytes
  - O valor da struct pode ser alterado

#### Alocação dinâmica de Struct
Assim como ponteiros, Struct podem ser alocadas dinamicamente, desta forma, criando uma lista de struct 

```c
struct ponto* p;
p = (struct ponto*) malloc (sizeof(struct ponto));
p->x = 12.0;
```

### Typedef
podemos criar mnemônicos para tipos de variaveis em C utilizando o comando **Typedef**
```c
typedef unsigned char UChar;
typedef int* PInt;
typedef struct ponto Ponto;
typedef struct pronto, *PPonto;
typedef struct ponto {
  float x;
  float y;
} Ponto, *PPonto;
```

### Tipo união
Em C podemos utilizar o tipo _union_ quando queremos armazenar valores heterongêneos numn mesmo espaço de memória. A definição de umna unição é parecida com a de um Struct

~~~c
union exemplo {
  int i;
  char c;
}

union examplo v;
v.i = 10;
~~~
ps: Apenas um elemnto de uma união pode estar armazenado num determ inado instante, pois a atribuição a um campo da união sobrescreve o valor anteiormente atribuído a qualquer outro campo

### Tipo enumeração

O tipo enumeração é um conjunsto de constantes inteiras com nomes que especifica os valores legais que uma variável dauqele tipo pode ter. É uma forma mais elegante de organizar valores constnates.

```c
enum bool {
  FALSE,
  TRUE
};
typedef enum bool Bool;
```

ps: por default os valores automaticamente dados no enum começam em 0, 1, 2 ...


___

## Tipos de dados

Algoritmo
- Uma sequência de ações expressas em termos de uma linguagem de programação, constituindo parte da solução de um tipo determinado de problema.
- descrição do padrão de comportamento associado aos **elementos funcionais ativos** de um processamento e deve ser expresso em termos de um conjunto finito de ações especificadas por meio de uma linguagem de programação.

Esturtura de Dados
- Dão suporte à descrições dos **elementos funcionais passivos** do padrão de comportamento, complementando o algoritmo que constitui parte da solução do problema considerado.
- Somado ao Algoritmo, compõem o *programa* a ser executado pelo computador

Programa
- Programar: Estruturar dados e construir algoritmos.
- Um programa é uma formulação concreta, em termos de uma linguagem de programação, de um procedimento abstrato que atua sobre um modelo de dados também abstrato. Ambos, procedimento e modelo de dados, são representações abstratas de algoritmo e estruturas de dados, respectivamente, e não devem ser expressos em termos de uma linguagem de programação.

Tipos de dados
- É importante classificar constantes, variáveis e valores g erados por expressões/funções de acordo com o seu tipo de dado
  - Caracteriza o conjunto de valores a que uma constnate pertence, os valores que uma variável pode assumir ou que pode ser gerado por uma expressão/função.

**Tipos de dados elementar(ou simples)**
- Caracterizado por um conjunto de valores indivisíveis
- int, float, char, bool...

**Tipo abstrato de dados**
Um modelo matemático que encapsula um _modelo de dados_ e um conjunto de _procedimentos_ que atuam com exclusividade sobre os dados encapsulados.

TAD:
- O domínio de um modelo matemático de dados
- um conjunto de oprações básicas que atuam com exclusividade sobre os valores desse domínio.
- Qualquer operação a ser realizada sobre dados definidos por meio dessa estrutura só poderá ser executada por intermédio dos algoritmos definidos no TAD

Partes necessárias de um TAD:
- Definição das estruturas de dados
- Definição do conjunto de algoritmos que implementam as opreções que atuam com exclusividade sobre essas estruturas de dados.

Um TAD bem construído pode tornar-se uma porção de código confiável e genérica, permitindo e aconselhando o seu reúso em outros programas.
  - aumenta a produtividade.
___

## Listas Simples
exemplo: Vetor.
- forma mais primitiva de representar diversos elementos agrupados.
- Ao declararmos um vetor, reservamos um espaço continuo de memória para armazenar seus elementos.
![vetores](https://miro.medium.com/max/875/1*smJVsUH4fDbrd6gd5mg9mg.jpeg)
- Podemos acessar qualquer um de seus elementos a partir do ponteiro para o primiero elemento.

cons:
- Não é muito flexível.
- Necessita saber o número máximo de elementos.
  - Se excedermos o limite, teremos um problema pois não existe uma maneira simples e barata (computacionalmente) para alterarmos a dimensão do vetor em tempo de execução.
  - Se o número de elementos utilizados for muito inferior à sua dimensão, estaremos sub-utilizando o espaço de memória reservado.

___

## Lista Encadeada
http://www.ic.uff.br/~cbraga/ed/apostila/ed10-listas.pdf


Em uma lista encadeada, para cada nvo elemento inserido na estrutura, alocamos um espaço de memória para armazená-lo
- O tamanho é proporcional ao número de elementos nela armazenada.
- Não podemos garantir que os elementos armazenados na lista ocuparão um espaço de momória contíguo.
- Para ser possível percorrer todos os elementos da lista, devemos explicitamente guardar o ponteiro para cada elemento.
  - junto com a informação de cada elemento, é armazenado um ponteiro para o próximo elemento da lista.
  - O último elemento da lista aponta para NULL, sinalizando que não existe um próximo elemento.
![Lista Encadeada](https://miro.medium.com/max/1300/1*ejbj1auh_Nxg_kmuuSGUSA.jpeg)

```c
struct lista
{
  int info;
  struct lista* prox;
};
typedef struct lista Lista;
```

Ps: Trata-se de uma lista auto-referenciada, temos (além da informação) há um campo que é um ponteiro para a próxima estrutura do mesmo tipo.


### Função de inicialização

A função que inicializa uma lista deve criar uma lista vazia.
- ferenciada pelo ponteiro NULL
```c
/* função de inicialização: retorna uma lista vazia */
Lista* inicializa (void)
{
return NULL;
}
```


### Função de inserção

Para cada elemento inserido na lista, devemos alocar dinamicamente a memória necessária oara armazenar o elemento e encadeá-lo na lista existente.
- A função mais simples insere o novo elemento no início da lista.

![Insere Lista](https://slideplayer.com.br/slide/16458201/96/images/13/Lista+encadeada+Implementa%C3%A7%C3%A3o%3A+inser%C3%A7%C3%A3o+no+in%C3%ADcio+da+lista+Lista%2A+ref.jpg)

```c
// insercao no inicio: retorna a lista atualizada
Lista* insere (Lista* l, int i){
  Lista* novo = (Lista*) malloc(sizeof(Lista));
  novo->info= i;
  novo->prox = l;
  return novo;
}

int main (void){
  Lista* l;
  l = inicializa();
  l = insere(l, 23);
  l = insere(l, 45);
  //...
  return 0;
}
```


### Funcao que percorre os elementos da lista
```c
// Funcao imprime: imprime os valores dos elementos
void imprime(Lista* l){
  Lista* p; //variavel auxiliar para percorrer a lista
  for (p = l;  p != NULL; p = p->prox){
    printf("info = %d\n", p->info)
  }
}

// OU de maneira RECURSIVA

int vazia (Lista *l){
  return (l == NULL);
}

void imprime_rec (Lista* l){
  if(vazia(l)){
    return;
  }
  //imprime primeiro o elemento da lista atual
  printf("info: %d\n", l->info);
  //imprime a sub-lista(a lista dos proximos elementos)
  imprime_rec(l->prox);
}
```


### Funcao que verifica se a lista esta vazia
- A função recebe a lista e retorna 1 se estiver vazia ou 0 se não estiver vazia.

```c
// funcao vazia: retorna 1 se vazia ou 0 se nao vazia
int vazia (Lista* l){
  if (l == NULL){
    return 1;
  }else{
    return 0;
  }
}
// forma compacta
int vazia (Lista* l){
  return (l == NULL);
}
```


### Funcao de Busca
- verificar se determinado elemento está presente na lista.
- returna o ponteiro do nó da lista que representa o elemento OU NULL caso o elemento não seja encontrado

```c
// busca um elemento na lista
Lista* busca (Lista* l, int v){
  Lista* p;
  for(p=l; p!=NULL; p=p->prox){
    if (p->info == v){
      return p;
    }
  }
  return NULL //não achou o elemento
}
```


### Função que retira um elemento da lista
- A função para retirar um elemento da lista é mais complexa.
  - Se descobrirmos que o elemento a ser retirado é o primeiro da lista
    - devemos fazer com que o novo valor da lista passe a ser o ponteiro para o segundo elemento, e então podemos liberar o espaço alocado para o segundo elemento
  - Se o elemento a ser removido estiver no meio da lista
    - devemos fazer com que o elemento anterior a ele passe a apontar para o elemento seguinte, e então podemos liberar o elemento.

![retirar elemento lista encadeada](http://albertocn.sytes.net/2012-1/ed1/aulas/figuras/lst_enc_remocao_meio.png)

```c
// Funcao retira um elemento da lista
Lista* retira (Lista* l, int v){
  Lista* ant = NULL //ponteiro para o elemento anterior
  Lista* p = l //ponteiro para percorrer a lista

  //procura elemento na lista, guardando anterior
  while (p != NULL && p->info != v){
    ant = p;
    p = p->prox;
  }
  
  //verifica se achou o elemento
  if (p == NULL){
    return l; //nao achou, retorna lista original
  }

  //retira elemento 
  if (ant == NULL){
    // do inicio
    l = p->prox;
  }
  else {
    //do meio
    ant-> prox = p->prox;
  }
  
  //libera o elemento encontrado
  free(p);
  return l;
}

// ou de maneira recursiva

Lista* retira_rec (Lista* l, int v){
  if (vazia(l))
    return l;
  
  // verifica se o valor a excluir e o primeiro
  if (l->info == v){
    Lista* t = l; //temporario para poder retirar
    l = l->prox;
    free(t);
  }else{
    //retira de sub-lista
    l->prox = retira_rec(l->prox,v);
  }

  return l;
}
```


### Funcao para librar a lista

- Libera todos os elementos alocados
  - Devemos guardar a referência para o próximo elemento antes de libera-lo

```c
void libera (Lista* l){
  Lista* p = l;
  while (p != NULL){
    Lista * t = p->prox; //guarda referência para o próximo elemento
    free(p); //libera a memoria apontada por p
    p = t; //faz p apontar para o prox elemento
  }
}


#include <stdio.h>
int main (void) {
  Lista* l; /* declara uma lista não iniciada */
  l = inicializa(); /* inicia lista vazia */
  l = insere(l, 23); /* insere na lista o elemento 23 */
  l = insere(l, 45); /* insere na lista o elemento 45 */
  l = insere(l, 56); /* insere na lista o elemento 56 */
  l = insere(l, 78); /* insere na lista o elemento 78 */
  imprime(l); /* imprimirá: 78 56 45 23 */
  l = retira(l, 78);
  imprime(l); /* imprimirá: 56 45 23 */
  l = retira(l, 45);
  imprime(l); /* imprimirá: 56 23 */
  libera(l);
  return 0;
}
```


### Inserir no meio

![inserir meio](https://slideplayer.com.br/slide/295671/1/images/11/Inserir+um+n%C3%B3+no+meio+da+lista.jpg)

Devemos:
- Localizar o elemento da lista que ira preceder o elemento novo
  - O elemento novo apontara para o proximo elemento na lista
  - O elemento precedente apontara para o novo

```C
Lista* cria (int v){
  Lista* p = (Lista*) malloc(sizeof(Lista));
  p->info = v;
  return p;
}
// funcao insere_ordenado
Lista* insere_ordenado(Lista* l, int v){

  Lista* novo = cria(v); //cria novo elemento
  Lista* ant = NULL; // ponteiro para o elemento anterior
  Lista* p = l; //ponteiro para percorrer a lista

  //procura prosicao de insercao (order crescente)
  while (p != NULL && p->info < v){
    ant = p;
    p = p->prox;
  }

  //insere elemento
  if (ant == NULL) {
    //insere no inicio
    novo->prox = l;
    l = novo;
  }else{
    //insere no meio
    novo->prox = ant->prox;
    ant->prox = novo;
  }
  return l;
}
```


## Listas circulares
O *ultimo elemento* tem como proximo elemento o **primeiro elemento da lista**.

A lista pode ser representada por um ponteiro para um elemento inicial qualquer da lista
![lista circular](https://slideplayer.com.br/slide/2995053/11/images/15/Lista+Encadeada+Circular.jpg)
Para percorrer os elementos:
- Visitamos todos os elementos a partir do ponteiro do elemento inicial, ate alcancarmos ele novamente

```c
void imprime_circular (Lista* l){
  Lista* p = l;
  
  if (p){
    do{
      printf("%d\n", p->info) //imprime a informacao do proximo no
      p = p->prox;
    }while(p != l);
  }
}

```


## Listas duplamente encadeadas
![listas duplamente encadeadas](https://sites.google.com/site/proffdesiqueiraed/_/rsrc/1472856774073/aulas/aula-6---listas-duplamente-encadeadas/Captura%20de%20tela%20de%202015-08-11%2015%3A00%3A14.png)

Cada elemento armazena **um** ponteiro para o **proximo** elemento e **um** ponteiro para o elemento **precedente**
- Podemos percorrer eficientemente os elementos em ordem inversa
- Facilita retira de elementos

```c
struct lista2{
  int info;
  struct lista2* ant;
  struct lista2* prox;
};
typedef struct lista2 Lista2;

```

### Funcao de insercao
![insercao](https://sites.google.com/site/proffdesiqueiraed/_/rsrc/1472856776256/aulas/aula-6---listas-duplamente-encadeadas/Captura%20de%20tela%20de%202015-08-11%2015%3A02%3A34.png)

```c
//insercao no inicio
Lista2* insere(Lista2* l, int v){
  Lista2* novo = (Lista2*) malloc(sizeof(Lista2));
  novo->info = v;
  novo->prox = l;
  novo->ant = NULL;
  //verifica se lista nao esta vazia
  if (l != NULL){
    l->ant = novo;
  }
  return novo;

}
```

### Funcao de busca
Recebe a informacao referente ao elemento que queremos buscar, e tem como valor de retorno o ponteiro do no da lista que representa o elemento.

Caso elemento nao seja encontrado, o valor retornado e NULL.
```c
//busca elemento na lista
Lista2* busca (Lista2* l, int v){
  Lista2* p;
  for(p=l, p!=NULL; p=p->prox){
    if(p->info == v){
      return p
    }
  }
  return NULL;
}


Lista2* busca_rec (Lista2* l, int v){
  if vazia(l){
    return NULL;
  }
  if (l->info == v){
    return l;
  }
  return busca_rec(l->prox, v);
}
```


### Funcao que retira um elemento
A funcao de remocao fica mais complicada, pois temos que acertar o encadeamento duplo.

Porem, podemos retirar um elemento conhecendo apenas o ponteiro para esse elemento.

```c
//funcao retirada
Lista2* retira (Lista2* l, int v){
  Lista2* p = busca(l,v);

  if (p == NULL)
    return l; //nao achou o elemento

  //retira elemento do encadeamento
  if (l==p){
    //o elemento e o primeiro elemento
    l = p->prox;
  }else{
    //tem um elemnto anterior, e ele deve apontar para o proximo
    p->ant->prox = p->prox;
  }

  //se tiver um elemento apos o elemento a ser retirado,
  if(p->prox != NULL){
    p->prox->ant = p->ant;
  }

  free(p);

  return l;
}

```

___


## Lista circular duplamente encadeada
O ultimo elemento passa a ter como proximo o primeiro elmento, que por sua vez passa a ter o ultimo elemento como anterior
- podemos percorrer a lista nos dois sentidos, a aprtir de qualquer ponto

```c
void imprime_circular_rev (Lista2* l){
  Lista2* p = l; /* faz p apontar para o nó inicial */
  /* testa se lista não é vazia */
  if (p) {
    /* percorre os elementos até alcançar novamente o início */
    do {
    printf("%d\n", p->info); /* imprime informação do nó */
    p = p->ant; /* "avança" para o nó anterior */
    } while (p != l);
  }
}

```

___

## Pilhas
http://www.ic.uff.br/~cbraga/ed/apostila/ed11-pilhas.pdf
![pilha](https://osprogramadores.com/img/conteudos-de-artigos/lifo_stack.png)

Todo o acesso a seus elementos e feito **atraves do seu topo**
- Insere elementos no topo
- Remove elementos do topo
**LIFO**: Last in, first out (primeiro que sai, ultimo que entrou)

### Pilhas com vetor
Em aplicacoes computacionais e comm saermos de antemao o numero maximo de elementos que podem estar arazenados simultaneamente na pilha.

```c
#define MAX 50

struct pilha {
  int n;
  float vet[MAX];
};
typedef struct pilha Pilha;

Pilha* cria (void){
  Pilha* p = (Pilha*) malloc(sizeof(Pilha));
  p->n = 0; //inicializa com 0 elementos
  return p
}

int vazia (Pilha* p){
  return (p->n == 0);
}

void libera (Pilha* p){
  free(p);
}

void push (Pilha* p, float v){
  if (p->n == MAX){
    printf("Capacidade da pilha estourou.\n");
    exit(1);
  }
  //insere elemento na proxima posicao livre
  p->vet[p->n] = v;
  p->n++;
}

//retira o elemento do topo da pilha, fornecendo seu valor como retorno
float pop (Pilha* p){
  float v;
  if (vazia(p)){
    printf("Pilha vazia.\n");
    exit(1);
  }
  //n e a proxima posicao de insercao.
  //n-1 e a posicao do ultimo elemento inserido
  v = p->vet[p->n-1];
  p->n--;
  return v;
  //retira elemento do topo
}

void imprime (Pilha* p){
  int i;
  for (i=p->n-1; i>=0; i--){
    printf("%f\n", p->vet[i]);
  }
}
```


### Pilha com lista
Usado quando: O numero maximo de elementos que serao armazenados na pilha nao e conhecido.

```c
//o no da lista para armazenar valores reais
struct no {
  float info;
  struct no* prox;
};
typedef struct no No;

//struct da pilha
struct pilha {
  No*  prim;
};
typedef struct pilha Pilha;

int vazia (Pilha* p){
  return(p->prim == NULL);
}

//inicialzia a pilha como vazia
Pilha* cria(void){
  Pilha* p = (Pilha*) malloc(sizeof(Pilha));
  p->prim = NULL;
  return p;
}

// func aux: insere no inicio
No* ins_ini (No* l, float v){
  No* p = (No*) malloc(sizeof(No));
  p->info = v;
  p->prox = l;
  return p;
}
//func aux: retira do inicio
No* ret_ini (No* l){
  No* p = l->prox;
  free(l);
  return p;
}

void push(Pilha* p, float v){
  p->prim = ins_ini(p->prim, v);
}

float pop (Pilha* p){
  float v;
  if (vazia(p)){
    printf("Pilha vazia.\n");
    exit(1);
  }
  v = p->prim->info;
  p->prim = ret_ini(p->prim);
  return v;
}

void libera(Pilha* p){
  No* q = p->prim;{
    while (q!=NULL){
      No* t = q->prox;
      free(q);
      q = t;
    }
  }
  free(p)
}

void imprime (Pilha* p){
  No* q;
  for (q = p->prim; q!=NULL; q=q->prox){
    printf("%f\n",q->info);
  }
}
```

___


## Filas
http://www.ic.uff.br/~cbraga/ed/apostila/ed12-filas.pdf
![filas](https://www.cos.ufrj.br/~rfarias/cos121/operacoesFila1.png)

Filas: O primeiro que entra e o primeiro que sai (queue) 
- **FIFO**: First In, First Out.
  - So podemos *inserir* um novo elemento no **final** da fila
  - so podemos *retirar* um elemento do **inicio** da fila


### Filas com Vetor
- Em um momento, a posicao inicio chegara na posicao fim, por este motivo e necessario emplementar uma logica circular no vetor

```c
#define N 100

struct fila {
  int ini, fim;
  float vet[N];
};
typedef struct fila Fila;

//funcao aux incrementar o indice do vetor de forma circular
int incr(int i){
  return (i+1)%N;
}

Fila* cria(void){
  fila* f = (Fila*) malloc(sizeof(Fila));
  f->ini = f->fim = 0; //lista vazia
  return f;
}

void insere (Fila* f, float v){
  if (incr(f->fim)==f->ini){
    printf("capacidade da fila estourou. \n);
    exit(1);
  }
  //insere elemento na proxima posicao livre
  f->vet[f->fim] = v;
  f->fim = incr(f->fim);
}

float retira (Fila* f){
  float v;
  if (vazia(f)){
    printf("Fila vazia\n");
    exit(1);
  }
  //retira elemento do inicio
  v = f->vet[f->ini];
  f->ini = incr(f->ini);
  return v;
}

int vazia (Fila* f){
  return (f->ini == f->fim);
}

void libera (Fila* f){
  free(f);
}

void imprime (Fila* f){
  int i;
  for (i=f->ini; i!=f->fim; i=incr(i)){
    printf("%f\n",f->vet[i]);
  }
}

```


### filas com lista
E uma lista encadeada em que cada no guarda um ponteiro para o proximo no da lista.

Usaremos dois ponteiros, ini e fim para retirarmos e inserirmos.
![filas listas](https://sites.google.com/site/proffdesiqueiraed/_/rsrc/1472856775084/aulas/aula-7---filas/Captura%20de%20tela%20de%202015-10-14%2017%3A05%3A15.png)


```c
struct no {
  float info;
  struct no* prox;
};
typedef struct no No;

struct fila{
  No* ini;
  No* fim;
};
typedef struct fila Fila;

Fila* cria(void){
  Fila* f = (Fila*) malloc(sizeof(Fila));
  f->ini = f->fim = NULL;
  return f;
}

// func aux: insere no fim
No* ins_fim (No* fim, float v){
  No* p = (No*) malloc(sizeof(No));
  p->info = v;
  p->prox = NULL;
  //verifica se a lista nao estava vazia.
  if(fim != NULL)
    fim->prox = p;
  return p;

}

//func aux: remove do inicio
No* ret_ini(No* ini){
  No* p = ini->prox;
  free(ini);
  return p;
}

void insere (Fila* f, float v){
  f->fim = ins_fim(f->fim, v);
  if (f->ini == NULL){
    //fila estava vazia?
    f->ini = f->fim;
  }
}

void retira (Fila* f){
  float v;
  if (vazia(f)){
    printf("fila vazia"\n);
    exit(1)
  }
  v = f->ini->info;
  f->ini = ret_ini(f->ini);
  
  if (f->ini == NULL){
    //fila ficou vazia?
    f->fim = NULL;
  }
  return v;
}

int vazia (Fila* f){
  return (f->ini == NULL);
}

void libera (Fila* f){
  No* q = f->ini;
  while (q != NULL){
    No* t = q->prox;
    free(q);
    q = t;
  }
  free(f);
}

void imprime (Fila* f){
  No* q;
  for (q=f->ini; q!=NULL; q=q->prox){
    printf("%f\n", q->info);
  }
}

```


___


## Deque (fila dupla)
http://www.ic.uff.br/~cbraga/ed/apostila/ed12-filas.pdf 12.4

A estrutura ***fila dupla*** consiste numa fila na qual e possivel inserir novos elementos **em ambas as extremidads**

consequentemente, permite-se tambem retirar elementos *de ambos os extremos*

![deque](https://media.geeksforgeeks.org/wp-content/uploads/anod.png)

### Deque (fila dupla) com vetor


### Deque (fila dupla) com lista
![deque lista](https://media.geeksforgeeks.org/wp-content/uploads/deque_dll.jpg)

Devemos usar uma lista duplamente encadeada, para solucionar o problema de retirar no fim da lista.

```c
struct no2{
  float info;
  struct no2* ant;
  struct no2* prox;
};
typedef struct no2 No2;

struct fila2 {
  No2* ini;
  No2* fim;
};
typedef struct fila2 Fila2;

// func aux: insere no inicio
No2* ins2_ini (No2* ini, float v){
  No2* p = (No2*) malloc(sizeof(No2));
  p->info = v;
  p->prox = ini;
  p->ant = NULL;
  
  //lista esta vazia?
  if (ini != NULL)
    int->ant = p;
  return p;
}

//func aux: insere no fim
No2* ins2_fim (No2* fim, float v){
  No2* p = (No2*) malloc(sizeof(No2));
  p->info = v;
  p->prox = NULL;
  p->ant = fim;

  //lista tem elemento?
  if (fim != NULL)
    fim->prox = p;
  return p;
}

//func aux: retira no inicio
No2* ret2_ini (No2* ini){
  No2* p = ini->prox;
  if (p != NULL){
    //lista tem elementos?
    p->ant = NULL;
  }
  free(ini);
  return p;
}

//func aux: retira no fim
No2* ret2_fim (No2* fim){
  No2* p = fim->ant;;
  if ( p != NULL){
    //lista tem elementos?
    p->prox = NULL;
  }
  free (fim);
  return p;
}

void insere_ini (Fila* f, float v){
  f->ini = ins2_ini(f->ini, v);
  if (f->fim == NULL){
    //fila vazia?
    f->fim = f->ini;
  }
}

void insere_fim (Fila* f, float v){
  f->fim = ins2_fim(f->fim, v)
  if(f->ini == NULL){
    f->ini = f->fim;
  }
}

float retira_ini(fila2* f){
  float v;
  if (vazia(f)){
    printf("fila vazia\n");
    exit(1)
  }
  v = f->fim->info;
  f->ini = ret2_ini(f->ini);
  if (f->ini == NULL){
    //fila ficou vazia?
    f->fim = NULL;
  }
  return v;
}

float retira_fim(Fila2* f){
  float v;
  if (vazia(f)){
    printf("Fila vazia\n")
    exit(1)
  }

  v = f->fim->info;
  f->fim = ret2_fim(f->fim);
  if (f->fim == NULL){
    //fila ficou vazia?
    f->ini = NULL;
  }
  return v;
}

```
