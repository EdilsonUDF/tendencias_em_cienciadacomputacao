# Prompt INicial Refinado
Atue como um **Revisor Sênior de Qualidade de Software especializado em Python**.

Revise o código Python abaixo e avalie sua qualidade de forma objetiva. Não considere apenas se o código funciona: verifique também sua organização, legibilidade, possíveis erros e boas práticas.

Durante a análise, considere principalmente:

1. **Legibilidade e organização** – nomes de variáveis e funções, indentação e estrutura do código.
2. **Erros e tratamento de entradas** – possíveis erros durante a execução e validação dos dados informados pelo usuário.
3. **Boas práticas de programação** – uso adequado de funções, variáveis e estruturas do Python.
4. **Manutenção e testabilidade** – se o código é fácil de entender, alterar e testar.
5. **Possíveis melhorias** – apresente sugestões práticas para deixar o código melhor.

Para cada problema encontrado:

* Informe qual é o problema;
* Explique por que ele pode ser prejudicial;
* Classifique a gravidade como **Baixa, Média ou Alta**;
* Mostre, quando possível, como corrigir.

Ao final, informe uma **nota de 0 a 10** para a qualidade geral do código e explique brevemente o motivo da nota.

Depois da análise, apresente uma **versão refatorada do código**, mantendo a mesma finalidade do programa, mas corrigindo os principais problemas encontrados.

### Formato da resposta

**Nota Geral:** X/10

### Problemas encontrados

1. **Problema:** ...

    * **Gravidade:** ...
    * **Por que é um problema:** ...
    * **Como melhorar:** ...

### Pontos positivos

* ...

### Sugestões gerais

* ...

### Código refatorado

```python
# código corrigido aqui
```

### Código para análise

```python
usuarios = []

def cadastrar(nome, idade):
    if idade > 0:
        usuarios.append({"nome": nome, "idade": idade})
    else:
        print("idade invalida")

def buscar(nome):
    for usuario in usuarios:
        if usuario["nome"] == nome:
            return usuario

while True:
    nome = input("Nome: ")
    idade = int(input("Idade: "))

    cadastrar(nome, idade)

    continuar = input("Cadastrar outro? ")

    if continuar == "nao":
        break

print(usuarios)
```
