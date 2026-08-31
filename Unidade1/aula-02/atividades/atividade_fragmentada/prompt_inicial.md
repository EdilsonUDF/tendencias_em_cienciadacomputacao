# Prompt Inicial

Revise o código Python abaixo e diga se ele está bom em relação à qualidade. 
Código: [
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

print(usuarios)]


