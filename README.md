# projetoDIOpython
Modelo de extrato bancário

menu = """
[d] = deposito
[s] = saque
[e] = extrato
[q] = sair 

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:
 
 opcao = input(menu)

 if opcao == "d":
 
    valor = float(input("informe o valor de deposito: "))
 
    if valor > 0:
       saldo =+ valor
       extrato == f"deposito: R$ {valor:.2f}\n"

    else:
       print("Operação falhou! O valor informado invalido") 


 elif opcao == "s":

    valor = float(input("informe o valor de saque"))
        
    if valor > 0:
       
       excedeu_saldo = valor > saldo

       excedeu_limite = valor > limite

       excedeu_saques = numero_saques >= LIMITE_SAQUES

    if excedeu_saldo:
       print("operação falhou! voce não possui saldo suficiente")
       
    elif excedeu_limite:
       print("operação falhou! voce excedeu o limite")
    
    elif excedeu_saques:
       print("operação falhou! voce excedeu o limite de saque")

    elif valor > 0:
         saldo -= valor
         extrato += f"saque: R$ {valor:.2f}\n"
         numero_saques += 1

    else:
      print("Operação falhou! O valor informado é inválido.")
   
 elif opcao == "e":
   print("\n---------------EXTRATO--------------")
   print("Não foram realizado movimentações." if not extrato else extrato)
   print(f"\nSaldo: R$ {saldo:.2f}")
   print("--------------------------------------")

 elif opcao =="q":
    break
 
 else:
    print("Operação inválida, por favor selecione novamente a operação desejada")
