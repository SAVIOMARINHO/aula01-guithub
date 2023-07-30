menu ="""
[d] Deposito
[s] Saque
[e] Extrato
[q] Sair

->"""

saldo = 0
limite = 500
extrato = ''
numeros_saque = 0
LIMITE_SAQUES = 3

while True:
    opcao = str(input(menu))

    if opcao == 'd':
        deposito = int(input('Deposito: '))

        if deposito > 0:
            saldo += deposito
            extrato += f'Deposito: {deposito}\n'
            print(f'Realizado o deposito: {deposito} R$')
        elif  deposito  == 0:
            print(f'Não e possivel realizar o deposito: {deposito} R$')
        else:
            print(f'Não e possivel realizar o deposito de valores negativos')

    elif opcao == 's':
        saque = int(input('Saque: '))

        if saque <= saldo:
            if saque > 0:
                if saque <= limite:
                    if numeros_saque < LIMITE_SAQUES:
                        saldo -= saque
                        numeros_saque += 1
                        extrato += f'Saque: {saque}\n'
                        print(f'Saque de: {saque} R$')
                    else:
                        print(f'A quantidade de saque diario ultrapassou a {LIMITE_SAQUES}') 

                else:
                    print(f'O valor do saque ultrapassa o valor maximo por saque: {limite} R$')
            else:
                print('Saque indisponivel para valores 0 e negativos')
        else:
            print('Saldo indisponivel')

    
    elif opcao == 'e':
        print(f'Extrato: {extrato}Saldo: {saldo}')

    elif opcao == 'q':
        break
 
    else:
        print('Operação inválida, por favor seleciona novamente a opção desejada.')

    
