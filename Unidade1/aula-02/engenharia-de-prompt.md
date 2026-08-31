# Aula 02 — Engenharia de Prompt

### Atividade Avaliativa A2 — Estudo de Caso em Qualidade de Software

## 1. Identificação

- **Disciplina:** Tendências em Ciências da Computação
- **Turma:** Ciência da Computação
- **Grupo:** Edilson Filho
- **Data:** 31/08/2026
- **Integrante:** Edilson Filho
- **Ferramenta de IA generativa utilizada:** ChatGPT (OpenAI), modelo GPT-5.6 Luna

## 2. Problema escolhido

### Contexto

A qualidade de software é um fator importante durante o desenvolvimento de aplicações. Um código pode funcionar corretamente em situações simples, mas ainda apresentar problemas relacionados à organização, legibilidade, validação de dados, manutenção e possibilidade de testes.

Durante o desenvolvimento, principalmente em projetos menores ou acadêmicos, é comum avaliar um código apenas pelo fato de ele executar sem erros aparentes. Porém, a qualidade de software envolve outros aspectos, como tratamento adequado de entradas, organização das funções, redução de dependências desnecessárias e facilidade de manutenção.

### Problema

Como realizar uma análise mais detalhada da qualidade de um código Python, identificando não apenas se ele funciona, mas também possíveis problemas relacionados à legibilidade, validação, boas práticas e manutenção?

### Objetivo

Utilizar IA generativa para revisar a qualidade de um código Python, identificar problemas, avaliar sua gravidade e propor melhorias através de uma versão refatorada.

> **Por que esse caso combina análise e refinamento de prompt?**
>
> A primeira resposta da IA realiza uma análise simples e genérica do código. Após identificar limitações nessa resposta, um novo prompt foi estruturado com critérios específicos de qualidade de software, níveis de gravidade e um formato de saída definido. Dessa forma, foi possível comparar como a estrutura do prompt influencia diretamente a profundidade da análise.

## 3. Prompt inicial

```text
Revise o código Python abaixo e diga se ele está bom em relação à qualidade.

Código:

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
````

## 4. Resultado inicial

```text
O código funciona, mas existem alguns pontos que podem ser melhorados.

* Os nomes das funções e variáveis poderiam ser mais descritivos.
* Poderia haver tratamento de erros para entradas inválidas.
* A função `buscar()` não possui um retorno caso o usuário não seja encontrado.
* Seria interessante adicionar comentários para facilitar a compreensão.
* O código poderia ser organizado de uma maneira melhor.

No geral, o código está funcionando, mas pode ser melhorado em relação à organização, tratamento de erros e legibilidade.
```

A resposta inicial identificou alguns problemas relevantes relacionados à qualidade do código, principalmente envolvendo organização, tratamento de entradas e legibilidade.

No entanto, a análise foi relativamente genérica e não apresentou uma avaliação detalhada sobre cada problema encontrado.

## 5. Análise crítica

* **O que funcionou:** a IA conseguiu identificar problemas básicos relacionados à qualidade do código, como ausência de tratamento de erros, necessidade de melhorar a organização e limitações na função `buscar()`.
* **O que não funcionou:** a resposta não realizou uma análise aprofundada do código e não explicou detalhadamente por que cada problema poderia prejudicar a aplicação.
* **O que faltou:** faltaram critérios claros de avaliação, classificação da gravidade dos problemas, sugestões concretas de correção, uma nota geral para o código e uma versão refatorada.
* **O que precisa ser validado:** é necessário verificar se os problemas identificados realmente representam riscos para o funcionamento e manutenção do programa e se as sugestões propostas mantêm a finalidade original do código.

## 6. Prompt refinado

````text
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
````

## 7. Resultado refinado

```text
O código cumpre a finalidade básica e é relativamente simples de entender, mas existem alguns pontos importantes relacionados principalmente à validação de entrada, organização e manutenção.

Nota Geral: 7/10

Problemas encontrados

Problema: Falta de tratamento para idade inválida

Gravidade: Média

Por que é um problema: A conversão int(input(...)) pode gerar um ValueError caso o usuário informe algo que não seja um número, como "vinte". Nesse caso, o programa será encerrado.

Como melhorar: Utilizar try/except para tratar entradas inválidas.

try:
    idade = int(input("Idade: "))
except ValueError:
    print("Digite uma idade válida.")


Problema: A função buscar() nunca é utilizada

Gravidade: Baixa

Por que é um problema: A função foi criada, mas não existe nenhuma chamada para ela no programa. Isso deixa código desnecessário e pode gerar dúvida sobre sua finalidade.

Como melhorar: Se a busca não faz parte da funcionalidade atual, remover a função. Caso seja necessária, criar uma opção no programa para utilizá-la.


Problema: A função buscar() não deixa explícito o que acontece quando não encontra o usuário

Gravidade: Baixa

Por que é um problema: Quando nenhum usuário é encontrado, a função retorna implicitamente None. Isso funciona, mas não deixa o comportamento tão explícito.

Como melhorar: Adicionar return None ao final.

def buscar(nome):
    for usuario in usuarios:
        if usuario["nome"] == nome:
            return usuario

    return None


Problema: A validação da idade é muito limitada

Gravidade: Média

Por que é um problema: O código verifica apenas se a idade é maior que zero. Assim, valores como 999 seriam aceitos.

Como melhorar: Definir uma faixa razoável para a idade, caso isso faça sentido para a aplicação.

if 0 < idade <= 120:
    usuarios.append({"nome": nome, "idade": idade})


Problema: Nome vazio pode ser cadastrado

Gravidade: Média

Por que é um problema: O usuário pode simplesmente pressionar Enter e cadastrar um registro com nome vazio.

Como melhorar: Validar o nome antes do cadastro.

if not nome.strip():
    print("O nome não pode ficar vazio.")
    return


Problema: A função cadastrar() depende diretamente da variável global usuarios

Gravidade: Média

Por que é um problema: Isso cria um acoplamento entre a função e o restante do programa. Em projetos maiores, fica mais difícil testar a função isoladamente.

Como melhorar: Passar a lista como parâmetro ou encapsular os dados em uma classe.

def cadastrar(usuarios, nome, idade):
    ...


Problema: A comparação de "nao" é muito rígida

Gravidade: Baixa

Por que é um problema: Entradas como "Não", "NAO" ou "não" não encerrariam o programa.

Como melhorar: Normalizar a entrada.

continuar = input("Cadastrar outro? ").strip().lower()

if continuar == "não":
    break


Problema: Não existe uma estrutura principal para executar o programa

Gravidade: Baixa

Por que é um problema: Todo o código é executado imediatamente ao importar o arquivo. Isso dificulta reutilização e testes.

Como melhorar: Colocar a execução em uma função main() e utilizar:

if __name__ == "__main__":
    main()


Pontos positivos

* O código é simples e fácil de compreender.
* Os nomes cadastrar e buscar são claros e representam bem suas funções.
* O uso de uma lista de dicionários é adequado para um programa pequeno.
* A função cadastrar() já possui uma validação básica da idade.
* Existe uma tentativa de separar responsabilidades através das funções cadastrar() e buscar().
* A estrutura for utilizada na busca é simples e adequada para uma lista pequena.


Sugestões gerais

* Criar uma função main() para organizar o fluxo principal.
* Validar todas as entradas fornecidas pelo usuário.
* Evitar variáveis globais quando possível.
* Normalizar entradas de texto com .strip().lower().
* Utilizar mensagens mais claras para erros.
* Caso o programa cresça, considerar uma classe para representar os usuários.
* Criar testes para as funções cadastrar() e buscar().
* Remover funções que não são utilizadas ou implementar uma funcionalidade que faça uso delas.
```

### Código refatorado

```python
usuarios = []


def cadastrar(usuarios, nome, idade):
    """Cadastra um novo usuário após validar os dados."""

    nome = nome.strip()

    if not nome:
        print("O nome não pode ficar vazio.")
        return False

    if idade <= 0 or idade > 120:
        print("Idade inválida.")
        return False

    usuarios.append({
        "nome": nome,
        "idade": idade
    })

    print("Usuário cadastrado com sucesso.")
    return True


def buscar(usuarios, nome):
    """Busca um usuário pelo nome."""

    nome = nome.strip().lower()

    for usuario in usuarios:
        if usuario["nome"].lower() == nome:
            return usuario

    return None


def main():
    while True:
        nome = input("Nome: ")

        try:
            idade = int(input("Idade: "))
        except ValueError:
            print("Digite uma idade válida.")
            continue

        cadastrar(usuarios, nome, idade)

        continuar = input("Cadastrar outro? ").strip().lower()

        if continuar in ("não", "nao"):
            break

    print("\nUsuários cadastrados:")

    for usuario in usuarios:
        print(f"Nome: {usuario['nome']} | Idade: {usuario['idade']}")


if __name__ == "__main__":
    main()
```

A resposta refinada apresentou uma análise mais detalhada e estruturada. Além de identificar os problemas, a IA explicou suas consequências, classificou suas gravidades e apresentou sugestões práticas de melhoria.

> **Validação do resultado:** a análise gerada pela IA deve ser avaliada criticamente. Algumas recomendações dependem do contexto da aplicação, como limitar a idade a 120 anos ou utilizar uma lista como parâmetro em vez de uma variável global. A versão refatorada também precisa ser executada e testada para garantir que mantém corretamente a finalidade original do programa.

## 8. Técnicas utilizadas

* [x] Role Prompting
* [ ] Few-Shot Prompting
* [x] Contexto
* [x] Restrições
* [x] Formato de saída
* [x] Prompt em etapas
* [x] Refinamento iterativo
* [ ] Outra

## 9. Comparação

| Critério                   | Prompt A (inicial) | Prompt B (refinado)                    |
| -------------------------- | ------------------ | -------------------------------------- |
| Clareza                    | Baixa              | Alta                                   |
| Contexto                   | Pouco específico   | Especializado em qualidade de software |
| Profundidade da análise    | Básica             | Detalhada                              |
| Organização                | Genérica           | Estruturada                            |
| Identificação de problemas | Limitada           | Mais completa                          |
| Classificação de gravidade | Não possui         | Baixa, Média ou Alta                   |
| Sugestões de melhoria      | Genéricas          | Práticas e específicas                 |
| Resultado final            | Apenas análise     | Análise e código refatorado            |

**Qual prompt produziu o resultado mais adequado? Por quê?**

O Prompt B produziu o resultado mais adequado porque definiu claramente o papel que a IA deveria assumir, os critérios que deveriam ser analisados e o formato esperado para a resposta.

Enquanto o primeiro prompt apenas solicitava uma opinião geral sobre a qualidade do código, o prompt refinado direcionou a análise para aspectos específicos, como legibilidade, tratamento de erros, boas práticas, manutenção e testabilidade.

Além disso, a definição de gravidade para cada problema e a solicitação de uma versão refatorada fizeram com que a resposta fosse mais útil e prática para compreender como o código poderia ser melhorado.

## 10. Teste de robustez

Para observar como uma alteração no prompt poderia influenciar o resultado, foi considerado alterar o papel definido para a IA.

* **Versão A:** Revisor Sênior de Qualidade de Software especializado em Python.
* **Versão B:** Desenvolvedor Python responsável por revisar o código.
* **O que mudou na resposta:** a alteração do papel pode modificar o foco da análise. Um revisor de qualidade tende a enfatizar critérios, riscos, manutenção e boas práticas, enquanto um desenvolvedor pode concentrar mais atenção na implementação e na forma de corrigir o código.
* **Por que acreditamos que mudou:** o papel atribuído à IA influencia a perspectiva utilizada para analisar o problema e priorizar determinados aspectos.
* **A alteração melhorou ou piorou o resultado?** Para o objetivo desta atividade, o papel de Revisor Sênior de Qualidade de Software é mais adequado, pois o foco principal não é apenas corrigir o código, mas avaliar sua qualidade de forma crítica e estruturada.

## 11. Validação

O resultado refinado foi analisado comparando os problemas apontados pela IA com o código original.

Foi considerado necessário verificar principalmente:

* se uma entrada não numérica realmente gera erro durante a conversão para `int`;
* se a função `buscar()` está sendo utilizada no fluxo do programa;
* se o código permite cadastrar nomes vazios;
* se a validação da idade é suficiente para o contexto da aplicação;
* se a variável global dificulta a manutenção e os testes;
* se a normalização da resposta do usuário melhora a experiência de utilização;
* se a versão refatorada mantém a mesma finalidade do programa original.

Também é necessário executar a versão refatorada e testar diferentes entradas, incluindo valores inválidos, nomes vazios e respostas diferentes para a opção de continuar o cadastro.

O resultado produzido pela IA não deve ser considerado automaticamente correto. As sugestões precisam ser analisadas de acordo com o contexto do software e testadas antes de serem aplicadas em um projeto real.

## 12. Ética e responsabilidade

* **Código incorreto:** a IA pode identificar problemas que não existem ou sugerir soluções inadequadas para determinado contexto. Por isso, recomendações automáticas precisam ser revisadas.
* **Confiança excessiva:** uma resposta detalhada não significa necessariamente que a análise esteja totalmente correta. A qualidade da explicação não substitui a validação técnica.
* **Responsabilidade profissional:** o desenvolvedor continua responsável pelas decisões tomadas e pelo código que será utilizado em um projeto.
* **Contexto da aplicação:** sugestões como limites de idade, estrutura de dados ou organização do código podem ser adequadas em um cenário e inadequadas em outro.
* **Dependência da IA:** a ferramenta deve ser utilizada como apoio para análise e aprendizado, sem substituir o conhecimento técnico e o pensamento crítico do profissional.

## 13. Take Away

### O que mudou na minha compreensão sobre o uso de IA depois de aprender a estruturar um prompt interativo?

Percebi que para obter uma boa resposta é necessário construir um bom prompt. A forma como o prompt é escrito faz bastante diferença no resultado gerado.

Quando foi definido um papel para a IA, explicado o que deveria ser analisado e especificado como a resposta deveria ser apresentada, o resultado ficou muito mais completo e organizado.

Também ficou claro que a IA é uma ferramenta que precisa ser bem orientada. Um prompt genérico pode produzir uma resposta genérica, enquanto instruções mais claras permitem direcionar melhor a análise.

### Qual é a principal responsabilidade de um profissional de tecnologia que utiliza IA generativa para tomar decisões ou produzir conhecimento?

A principal responsabilidade é sempre conferir e validar o resultado produzido pela IA, sem aceitar todas as informações como verdade.

A IA pode ajudar bastante no desenvolvimento de um projeto, na análise de código e até na produção de conhecimento, mas também pode cometer erros ou fornecer informações incorretas.

A responsabilidade continua sendo do profissional que está utilizando a ferramenta. A IA pode ajudar durante o processo, mas a decisão final precisa passar por uma análise humana e crítica.

## 14. Link
https://github.com/EdilsonUDF/tendencias_em_cienciadacomputacao.git
```
```