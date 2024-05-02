class ContaBancaria:
    def __init__(self, titular, numero_conta, saldo_inicial=0):
        self.titular = titular
        self.numero_conta = numero_conta
        self.saldo = saldo_inicial
        self.historico_transacoes = []

    def depositar(self, valor):
        if valor > 0:
            self.saldo += valor
            self.historico_transacoes.append(f"Depósito: R${valor:.2f}")
            print(f"Depósito de R${valor:.2f} realizado com sucesso.")
        else:
            print("Valor de depósito inválido.")

    def sacar(self, valor):
        if valor > 0:
            if valor <= self.saldo:
                self.saldo -= valor
                self.historico_transacoes.append(f"Saque: R${valor:.2f}")
                print(f"Saque de R${valor:.2f} realizado com sucesso.")
            else:
                print("Saldo insuficiente para saque.")
        else:
            print("Valor de saque inválido.")

    def extrato(self):
        print("\nExtrato de Transações:")
        for transacao in self.historico_transacoes:
            print(transacao)
        print(f"Saldo atual: R${self.saldo:.2f}\n")

def main():
    conta = ContaBancaria("João Silva", "12345", 1000)
    ativo = True

    while ativo:
        print("\nMenu:")
        print("[1] Depositar")
        print("[2] Sacar")
        print("[3] Extrato")
        print("[4] Sair")
        opcao = input("Escolha uma opção: ")

        if opcao == "1":
            valor = float(input("Valor do depósito: R$"))
            conta.depositar(valor)
        elif opcao == "2":
            valor = float(input("Valor do saque: R$"))
            conta.sacar(valor)
        elif opcao == "3":
            conta.extrato()
        elif opcao == "4":
            ativo = False
            print("Obrigado por usar nosso sistema bancário!")
        else:
            print("Opção inválida, tente novamente.")

if __name__ == "__main__":
    main()
