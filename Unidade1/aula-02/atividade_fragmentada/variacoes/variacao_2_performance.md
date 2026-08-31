# Prompt
Atue como um Revisor Sênior de QA. Analise o código Python fornecido e retorne somente um JSON válido com os seguintes campos:
{ "bugs": [], "code_smells": [], "sugestao_refatorada": "", "nota_0_a_10": 0 } 
Seja rigoroso na análise e considere problemas de qualidade, performance, segurança e organização do código.

# Resposta Performace
{
"bugs": [
{
"problema": "Indentação incorreta",
"gravidade": "critica",
"explicacao": "O código apresentado possui blocos sem a indentação necessária. Em Python, isso pode gerar IndentationError e impedir a execução do programa."
},
{
"problema": "Conversão direta da idade para inteiro",
"gravidade": "alta",
"explicacao": "A chamada int(input()) pode gerar ValueError caso o usuário informe um valor que não seja numérico, encerrando o programa."
},
{
"problema": "Nome não é validado",
"gravidade": "media",
"explicacao": "O programa permite que o usuário informe um nome vazio ou apenas espaços."
}
],
"code_smells": [
{
"problema": "Uso de variável global",
"explicacao": "A lista usuarios é acessada diretamente por diferentes funções, aumentando o acoplamento do código."
},
{
"problema": "Ausência de type hints",
"explicacao": "As funções não informam os tipos dos parâmetros nem dos valores retornados, reduzindo a clareza do código."
},
{
"problema": "Validação limitada",
"explicacao": "A idade é validada apenas para verificar se é maior que zero."
},
{
"problema": "Função buscar sem retorno explícito",
"explicacao": "Quando nenhum usuário é encontrado, a função termina sem um return explícito, retornando None implicitamente."
}
],
"sugestao_refatorada": "Corrigir a indentação, adicionar tratamento de ValueError para a entrada da idade, validar o nome, utilizar type hints e reduzir a dependência da variável global. Também é recomendado deixar explícito o retorno da função buscar.",
"nota_0_a_10": 5
}
