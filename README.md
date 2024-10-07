# Sistema-Bancario-DIO-NTT-Data
# Projeto Sistema Bancário DIO NTT Data

menu = """
--------------------Banco DIO-------------------
**************** Seja bem vindo! ***************
-------------------Conta Nomal------------------

Sistema iniciado...

⏩ Escolha uma das opções:

1️⃣  Depositar
2️⃣  Sacar
3️⃣  Extrato
4️⃣  Sair  
"""

class Banco:
    def __init__(self):
            self.saldo = 0.0
            self.extrato = []

    def depositar(self, valor):
        if valor > 0:
            self.saldo += valor
            self.extrato.append(f'Depósito: R${valor:.2f}')
            print(f'💰Depósito de R${valor:.2f} realizado com sucesso!')
        else:
            print('❌Valor de depósito deve ser positivo!')

    def sacar(self, valor):
        if valor > 0:
            if valor <= self.saldo:
                self.saldo -= valor
                self.extrato.append(f'Saque: R${valor:.2f}')
                print(f'💲Saque de R${valor:.2f} realizado com sucesso!')
            else:
                print('\n❌Saldo insuficiente para realizar o saque!')
        else:
            print('Valor de saque deve ser positivo!')

    def exibir_extrato(self):
        print("\n--- Extrato ---")
        if not self.extrato:
            print("Nenhuma operação realizada.\n")
        else:
            for operacao in self.extrato:
                print(operacao)
        print(f'💲Saldo atual: R${self.saldo:.2f}\n')


def main():
    banco = Banco()
    
    while True:
        print(menu)       
        
        opcao = input("⏩ Opção: ")

        if opcao == '1':
            valor = float(input("\n💰Informe o valor a depositar: "))
            banco.depositar(valor)
        elif opcao == '2':
            valor = float(input("\n💲Informe o valor a sacar: "))
            banco.sacar(valor)
        elif opcao == '3':
            banco.exibir_extrato()
        elif opcao == '4':
            print("Saindo... Até logo!")
            break
        else:
            print("Opção inválida! Tente novamente.")

if __name__ == "__main__":
    main()
