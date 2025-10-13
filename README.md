# Contagem e Plotagem | Estrutura de Dados


Este projeto analisa o número de **comparações realizadas** ao buscar elementos em uma **lista encadeada** e em uma **árvore binária de busca (BST)**, utilizando dados gerados aleatoriamente.  

Os resultados são exportados em formato CSV e visualizados por meio de um gráfico construído no **R (ggplot2)**.


---

## 🧩 Estrutura do Projeto

├── main.c    

├── dados.csv  

├── analise.R 

└── README.md 

---

## Como funciona

O programa em **C**:
- Cria duas estruturas de dados:
  - **Lista encadeada**
  - **Árvore binária de busca**
- Insere `n` números aleatórios (por padrão, 10.000 valores únicos)
- Busca os mesmos números nas duas estruturas, contando o número de **comparações** realizadas em cada busca
- Armazena os resultados no arquivo `dados.csv`, no formato:

| numero | comparacoes_lista | comparacoes_arvore |
|:-------|:------------------:|:------------------:|
| 4832   | 911                | 12                 |
| 829    | 754                | 9                  |

---

## Objetivo didático

O projeto permite **comparar o custo de busca** entre:
- **Listas encadeadas**, que exigem buscas lineares (O(n))
- **Árvores binárias de busca**, que idealmente têm buscas logarítmicas (O(log n))

Dessa forma, é possível visualizar empiricamente como a estrutura de dados impacta a eficiência da busca.

---

## Como compilar e executar

### 🔧 Compilação

Use o GCC ou outro compilador C:


gcc main.c -o comparacao

## ▶️ Execução

./comparacao

Ao final, o programa exibirá:

Arquivo 'dados.csv' gerado com sucesso!

## Interpretação do Gráfico

O gráfico mostra, de maneira geral, a média de comparações que precisam ser feitas para se encontrar um número dentro de estruturas de dados com tamanho fixo de 10.000 elementos.



## 🧩 Explicação das Funções (Código em C)

## Estruturas de Dados
typedef struct no_lista {
    int valor;
    struct no_lista *prox;
} NoLista;

typedef struct no_arvore {
    int valor;
    struct no_arvore *esq, *dir;
} NoArv;

NoLista representa um nó da lista encadeada, com um valor e um ponteiro para o próximo elemento.
NoArv representa um nó da árvore binária, com um valor e dois ponteiros (filho esquerdo e direito).

## Inserção na Lista
void insere_numeros_lista(NoLista **lista, int v);

Cria um novo nó e o insere no início da lista.
Operação simples, complexidade O(1).
O novo elemento aponta para o anterior, e o ponteiro principal da lista é atualizado.

## Busca na Lista
int busca_numeros_lista(NoLista *lista, int chave);

Percorre a lista do início ao fim, comparando cada nó com o valor procurado.
Conta o número de comparações até encontrar (ou não) o valor.
Complexidade: O(n) (linear).

## Inserção na Árvore
NoArv* insere_numeros_arv(NoArv *raiz, int v);

Insere um novo valor na árvore binária de busca (BST).
Valores menores vão para a subárvore esquerda; maiores, para a direita.
Implementação recursiva.
Complexidade: O(log n) em média, O(n) no pior caso (árvore degenerada).

## Busca na Árvore
int busca_numeros_arv(NoArv *raiz, int chave);

Percorre a árvore comparando o valor buscado com o nó atual:
Se for menor, vai para a esquerda.
Se for maior, vai para a direita.
Conta o número de comparações realizadas.
Complexidade: O(log n) em média.

## Embaralhamento dos números
void embaralha_numeros(int *v, int n);

Implementa o algoritmo Fisher–Yates Shuffle.
Garante que os números de 0 a n−1 fiquem em ordem aleatória.
Evita viés nas inserções e buscas.

## Função Principal
int main();

Etapas executadas:
Gera um vetor de total números (0 a 9999).
Embaralha o vetor.
Insere os primeiros n números na lista e na árvore.
Realiza novas buscas aleatórias nas duas estruturas.
Registra em dados.csv:
O número buscado
Quantas comparações foram necessárias em cada estrutura
Exibe mensagem de sucesso e libera a memória.

## 🧪 Tecnologias utilizadas
C → Implementação das estruturas e geração dos dados
R / ggplot2 → Análise e visualização dos resultados

## ✍️ Créditos
Projeto desenvolvido para fins didáticos, com foco em análise de estruturas de dados e visualização de desempenho.
<center>
Equipe:

  Jader Rogerio dos Santos Neto | Guilherme Nunes Alves | Carlos Antunis Bonfim de Silva Santos | Pedro Henrique Santos da Silva | Carlos Leonardo Rodrigues Novaes Carvalho

 </center>
