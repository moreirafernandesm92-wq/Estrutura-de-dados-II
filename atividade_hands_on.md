# Atividade Hands-on: Seja o Computador!

**Nome completo:** Maria Eduarda Moreira Fernandes  
**Matrícula:** 42781515  
**Turma:** Engenharia de Software  
**Disciplina:** Estrutura de Dados II - 166EstDa2TerD2  

---

## Etapa 1: Representação da Árvore

### Identificação dos Nós
* **Nó raiz:** 40
* **Filho esquerdo da raiz:** 20
* **Filho direito da raiz:** 60
* **Filhos do nó 20:** 10 (esquerda) e 30 (direita)
* **Filhos do nó 60:** 50 (esquerda) e 70 (direita)

| Nível | Nós |
|---|---|
| 0 | 40 |
| 1 | 20, 60 |
| 2 | 10, 30, 50, 70 |

### Esquema da Árvore Binária

```text
Nível 0 (Raiz):            40
                         /    \
Nível 1:               20      60
                      /  \    /  \
Nível 2:             10  30  50  70
```

---

## Etapa 2: Análise das Funções

| Função | Posição do `print()` | Regra do Percurso |
|---|---|---|
| `pre_ordem()` | Antes das chamadas recursivas | Raiz → Esquerda → Direita |
| `em_ordem()` | Entre as chamadas recursivas | Esquerda → Raiz → Direita |
| `pos_ordem()` | Depois das chamadas recursivas | Esquerda → Direita → Raiz |

---

## Etapa 3: Simulação da Pré-ordem

| Passo | Nó atual | Ação realizada | Valor impresso |
|---|---|---|---|
| 1 | 40 | Visitar o nó raiz | 40 |
| 2 | 20 | Visitar filho esquerdo de 40 | 20 |
| 3 | 10 | Visitar filho esquerdo de 20 | 10 |
| 4 | 30 | Visitar filho direito de 20 | 30 |
| 5 | 60 | Visitar filho direito de 40 | 60 |
| 6 | 50 | Visitar filho esquerdo de 60 | 50 |
| 7 | 70 | Visitar filho direito de 60 | 70 |

---

## Etapa 4: Saídas Previstas

* **Pré-ordem (`pre_ordem(raiz)`):**  
  `40 20 10 30 60 50 70`
* **Em-ordem (`em_ordem(raiz)`):**  
  `10 20 30 40 50 60 70`
* **Pós-ordem (`pos_ordem(raiz)`):**  
  `10 30 20 50 70 60 40`

---

## Etapa 5: Interprete o Código

1. **Qual função imprime o nó raiz primeiro?**  
   A função `pre_ordem()`.

2. **Qual função imprime o nó raiz por último?**  
   A função `pos_ordem()`.

3. **Em qual função o comando `print()` está localizado entre as duas chamadas recursivas?**  
   Na função `em_ordem()`.

4. **Qual percurso apresenta os valores em ordem crescente?**  
   O percurso `em_ordem()`, pois a estrutura montada é uma Árvore Binária de Busca (BST).

5. **Por que a condição `if no is not None:` é necessária?**  
   Representa o caso base da recursão. Ela impede que o programa tente acessar atributos de um objeto inexistente (`None`), o que causaria um erro de execução (`AttributeError`), além de interromper a cadeia de chamadas recursivas ao atingir as folhas.

6. **O que representa o parâmetro `no` recebido pelas funções?**  
   Representa a referência ao nó atual (ou raiz da subárvore corrente) que está sendo processado naquela chamada recursiva específica.

7. **O que acontece quando uma função recursiva encontra um filho com valor `None`?**  
   A condição `if no is not None:` é avaliada como falsa. A função não executa o bloco do `if`, finaliza a execução do quadro atual e devolve o controle para a função chamadora anterior na pilha de execução.

8. **Qual seria a saída Em-ordem se o nó 30 fosse removido?**  
   `10 20 40 50 60 70`

9. **Em que momento as chamadas recursivas começam a retornar?**  
   Quando a recursão atinge uma extremidade nula (`None`) nas folhas. A partir daí, as funções no topo da pilha de chamadas terminam e retornam o controle para os nós ancestrais acima.

10. **Explique, com suas palavras, a principal diferença entre os três percursos.**  
    A diferença fundamental está no momento (ou prioridade) em que o nó atual é visitado/impresso em relação aos seus filhos:
    * Na **Pré-ordem**, o nó pai é processado antes dos seus filhos.
    * Na **Em-ordem**, o nó pai é processado entre a navegação pelo filho esquerdo e pelo filho direito.
    * Na **Pós-ordem**, o nó pai é processado depois de ambos os seus filhos já terem sido processados.

---

## Etapa 6: Verificação no Google Colab

### Código de Implementação

```python
class No:
    def __init__(self, valor):
        self.valor = valor
        self.esquerda = None
        self.direita = None

def pre_ordem(no):
    if no is not None:
        print(no.valor, end=" ")
        pre_ordem(no.esquerda)
        pre_ordem(no.direita)

def em_ordem(no):
    if no is not None:
        em_ordem(no.esquerda)
        print(no.valor, end=" ")
        em_ordem(no.direita)

def pos_ordem(no):
    if no is not None:
        pos_ordem(no.esquerda)
        pos_ordem(no.direita)
        print(no.valor, end=" ")

# Construção da árvore
raiz = No(40)

raiz.esquerda = No(20)
raiz.direita = No(60)

raiz.esquerda.esquerda = No(10)
raiz.esquerda.direita = No(30)

raiz.direita.esquerda = No(50)
raiz.direita.direita = No(70)

# Execução dos percursos
print("Pré-ordem:")
pre_ordem(raiz)

print("\nEm-ordem:")
em_ordem(raiz)

print("\nPós-ordem:")
pos_ordem(raiz)
```

### Registro de Comparação para o Relatório

* **Saída Gerada pelo Computador:**  
  * **Pré-ordem:** `40 20 10 30 60 50 70`  
  * **Em-ordem:** `10 20 30 40 50 60 70`  
  * **Pós-ordem:** `10 30 20 50 70 60 40`  

* **Análise de Divergências:**  
  As saídas previstas manualmente nas etapas 3 e 4 coincidem integralmente com a saída gerada pelo computador. Não houve nenhuma divergência de interpretação das chamadas recursivas.
