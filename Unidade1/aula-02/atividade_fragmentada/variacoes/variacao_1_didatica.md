# Prompt
Atue como um Revisor Sênior de QA. 
Analise o código Python fornecido.

Seja rigoroso na análise e considere problemas de qualidade, performance, segurança e organização do código. 


# Resposta Didatica


O código tem a ideia de cadastrar usuários, armazenando o nome e a idade em uma lista. Porém, existem alguns problemas que precisam ser corrigidos.

### 1. Problema de indentação

O primeiro problema está na indentação do código:

```python
def cadastrar(nome, idade):
if idade > 0:
usuarios.append({"nome": nome, "idade": idade})
else:
print("idade invalida")
```

Em Python, a indentação é muito importante porque ela define quais comandos pertencem a uma função, condição ou repetição.

Nesse caso, o código deveria estar indentado desta forma:

```python
def cadastrar(nome, idade):
    if idade > 0:
        usuarios.append({"nome": nome, "idade": idade})
    else:
        print("idade invalida")
```

Se a indentação estiver exatamente como foi apresentada, o Python vai gerar um erro de sintaxe (`IndentationError`) e o programa nem conseguirá ser executado.

---

### 2. Falta de tratamento de erro na idade

Outro problema está nesta parte:

```python
idade = int(input("Idade: "))
```

O programa tenta transformar diretamente o que o usuário digitou em um número inteiro.

Por exemplo, se o usuário digitar:

```text
vinte
```

o programa vai gerar um erro e será encerrado.

Uma forma melhor seria utilizar `try` e `except`:

```python
try:
    idade = int(input("Idade: "))
except ValueError:
    print("Digite uma idade válida.")
```

Assim, o programa consegue tratar uma entrada inválida sem simplesmente parar.

---

### 3. Validação da idade

O código já possui uma validação:

```python
if idade > 0:
```

Isso é positivo, porque evita cadastrar uma idade igual a zero ou negativa.

Porém, seria interessante informar uma mensagem mais clara para o usuário e, dependendo da regra do sistema, estabelecer também um limite máximo.

Por exemplo:

```python
if 0 < idade <= 120:
    usuarios.append({"nome": nome, "idade": idade})
else:
    print("Digite uma idade válida.")
```

---

### 4. Uso de variável global

A lista `usuarios` foi criada fora das funções:

```python
usuarios = []
```

E depois é utilizada diretamente dentro de `cadastrar()` e `buscar()`.

Isso funciona nesse programa pequeno, mas pode causar dificuldades quando o projeto crescer, porque várias partes do programa passam a depender da mesma variável.

Uma alternativa seria passar a lista como parâmetro:

```python
def cadastrar(usuarios, nome, idade):
    ...
```

Dessa forma, fica mais claro de onde os dados estão vindo.

---

### 5. Função `buscar()` não informa quando não encontra o usuário

A função:

```python
def buscar(nome):
    for usuario in usuarios:
        if usuario["nome"] == nome:
            return usuario
```

procura o usuário e retorna quando encontra.

Porém, quando nenhum usuário possui aquele nome, a função termina sem retornar um valor.

Nesse caso, Python retorna `None` automaticamente.

Seria melhor deixar esse comportamento mais claro:

```python
def buscar(nome):
    for usuario in usuarios:
        if usuario["nome"] == nome:
            return usuario

    return None
```

---

### 6. Falta de validação do nome

O programa aceita qualquer coisa no campo nome.

Por exemplo, o usuário poderia simplesmente pressionar Enter e cadastrar:

```text
{"nome": "", "idade": 20}
```

Seria interessante verificar se o nome foi preenchido:

```python
nome = input("Nome: ").strip()

if not nome:
    print("O nome não pode ficar vazio.")
```

---

### Conclusão

O código possui uma estrutura simples e a ideia principal está correta, mas precisa de algumas melhorias para ficar mais seguro e organizado.

Os principais pontos são:

* Corrigir a indentação;
* Tratar entradas inválidas;
* Melhorar a validação da idade;
* Evitar depender diretamente de uma variável global;
* Melhorar a função de busca;
* Validar o nome informado pelo usuário.

Essas mudanças deixam o programa mais confiável e também mais fácil de manter.
te como foi apresentada, o Python vai gerar um erro de sintaxe (IndentationError) e o programa nem conseguirá ser executado.estiver exatamente como foi apresentada, o Python vai gerar um erro de sintaxe (IndentationError) e o programa nem conseguirá ser executado.regra é pensar no código como uma casa: se tudo estiver jogado no mesmo cômodo, pode até funcionar, mas fica muito mais difícil encontrar e consertar alguma coisa depois.