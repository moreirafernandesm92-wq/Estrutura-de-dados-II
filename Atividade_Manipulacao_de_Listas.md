# Atividade de Participação — Manipulação de Listas e Representação na Memória em Python

**Autores:**
- Maria Eduarda Moreira Fernandes — RGM: 42781515
- Arthur Santos Noleto — RGM: 44004567

---

## Código Python

```python
def mostrar_lista(passo, lista):
    print(passo)
    print("Conteudo:", lista)
    print("ID da lista:", id(lista))
    for i in range(len(lista)):
        print("Indice:", i, "| Valor:", lista[i], "| ID do elemento:", id(lista[i]))
    print("-" * 40)


lista = [10, 20, 30]
mostrar_lista("1. Lista inicial:", lista)

lista.append(40)
mostrar_lista("2. Apos append(40):", lista)

lista.insert(1, 15)
mostrar_lista("3. Apos insert(1, 15):", lista)

lista.remove(20)
mostrar_lista("4. Apos remove(20):", lista)

lista.pop(2)
mostrar_lista("5. Apos pop(2):", lista)

lista[0] = 99
mostrar_lista("6. Apos mudar lista[0] para 99:", lista)

lista.clear()
print("7. Apos clear():")
print("Conteudo:", lista)
print("ID da lista:", id(lista))
print("-" * 40)
```

---

## Evidências da execução

```
1. Lista inicial:
Conteudo: [10, 20, 30]
ID da lista: 137690016474560
Indice: 0 | Valor: 10 | ID do elemento: 11278216
Indice: 1 | Valor: 20 | ID do elemento: 11278536
Indice: 2 | Valor: 30 | ID do elemento: 11278856
----------------------------------------
2. Apos append(40):
Conteudo: [10, 20, 30, 40]
ID da lista: 137690016474560
Indice: 0 | Valor: 10 | ID do elemento: 11278216
Indice: 1 | Valor: 20 | ID do elemento: 11278536
Indice: 2 | Valor: 30 | ID do elemento: 11278856
Indice: 3 | Valor: 40 | ID do elemento: 11279176
----------------------------------------
3. Apos insert(1, 15):
Conteudo: [10, 15, 20, 30, 40]
ID da lista: 137690016474560
Indice: 0 | Valor: 10 | ID do elemento: 11278216
Indice: 1 | Valor: 15 | ID do elemento: 11278376
Indice: 2 | Valor: 20 | ID do elemento: 11278536
Indice: 3 | Valor: 30 | ID do elemento: 11278856
Indice: 4 | Valor: 40 | ID do elemento: 11279176
----------------------------------------
4. Apos remove(20):
Conteudo: [10, 15, 30, 40]
ID da lista: 137690016474560
Indice: 0 | Valor: 10 | ID do elemento: 11278216
Indice: 1 | Valor: 15 | ID do elemento: 11278376
Indice: 2 | Valor: 30 | ID do elemento: 11278856
Indice: 3 | Valor: 40 | ID do elemento: 11279176
----------------------------------------
5. Apos pop(2):
Conteudo: [10, 15, 40]
ID da lista: 137690016474560
Indice: 0 | Valor: 10 | ID do elemento: 11278216
Indice: 1 | Valor: 15 | ID do elemento: 11278376
Indice: 2 | Valor: 40 | ID do elemento: 11279176
----------------------------------------
6. Apos mudar lista[0] para 99:
Conteudo: [99, 15, 40]
ID da lista: 137690016474560
Indice: 0 | Valor: 99 | ID do elemento: 11281064
Indice: 1 | Valor: 15 | ID do elemento: 11278376
Indice: 2 | Valor: 40 | ID do elemento: 11279176
----------------------------------------
7. Apos clear():
Conteudo: []
ID da lista: 137690016474560
----------------------------------------
```

---

## Resultados Obtidos

- **A lista não muda de lugar na memória:** O ID da lista (137690016474560) ficou igual da primeira linha até a última, mesmo depois do `clear()`. Isso mostra que alterar uma lista não cria uma lista nova na memória, ela só altera o que tem dentro.
- **Os números só trocam de posição:** No `insert()` e no `remove()`, os números mudaram de índice, mas o ID de cada um continuou o mesmo. O número 30, por exemplo, manteve o ID 11278856 do começo ao fim, só mudando de índice.
- **Trocar o número cria outro ID:** Quando o 10 foi trocado pelo 99 na posição 0, o ID desse elemento mudou de 11278216 para 11281064. Isso é porque o Python cria um espaço novo na memória para guardar o 99 e faz o índice 0 apontar pra ele.
- **O `clear()` deixa a lista vazia, mas ela continua lá:** O comando limpou todos os itens da lista, mas ela continuou no mesmo endereço de memória que estava antes.

---

## Análise dos Resultados

**a)** Não, o ID da lista continuou 137690016474560 do começo ao fim. Isso indica que a lista é o mesmo objeto na memória e que todas as alterações aconteceram dentro dela, sem criar uma nova.

**b)** Os elementos que já estavam na lista continuaram com os mesmos IDs, mas mudaram de posição (índice) quando foi usado o insert. O novo valor adicionado ganhou um ID próprio na memória e foi colocado no índice indicado.

**c)** A lista deixa de apontar para aquele elemento, e os itens que vinham depois dele chegam uma posição para trás (reindexação). Se o elemento removido não estiver sendo usado em outra variável, o Python apaga ele da memória.

**d)** Não, o ID do elemento mudou de 11278216 (que era o 10) para 11281064 (que passou a ser o 99). Isso acontece porque números inteiros são imutáveis no Python: não se altera o número 10 para virar 99, a lista passa a guardar o endereço de um novo número 99.

**e)** Porque é possível adicionar, remover ou trocar itens de dentro dela mantendo sempre o mesmo endereço de memória, sem ter que recriar a lista do zero.

**f)** Alterar o conteúdo modifica a lista atual no mesmo espaço de memória (id). Criar uma nova lista reserva um espaço totalmente diferente na memória com um novo id, jogando fora ou deixando de lado a lista antiga.
