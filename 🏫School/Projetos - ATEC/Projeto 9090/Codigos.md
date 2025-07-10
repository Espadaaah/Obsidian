
# Main.py
---
```shell
from scan_ports import scan_ports
from active_connections import list_active_connections
from log_parser import parse_logs
from export_utils import export_data
from db_handler import initialize_db


def menu():
    initialize_db()

    while True:
        print("\n--- Projeto 9190 ---")
        print("1. Scan de ports em máquinas remotas")
        print("2. Ver conexões ativas")
        print("3. Analisar logs (SSH/HTTP)")
        print("4. Exportar dados")
        print("5. Sair")

        opcao = input("Escolha uma opção: ")

        if opcao == "1":
            ip = input("IP da máquina remota: ")
            try:
                start_port = int(input("Port inicial: "))
                end_port = int(input("Port final: "))
                if start_port > end_port or start_port < 1 or end_port > 65535:
                    print("Intervalo inválido.")
                else:
                    scan_ports(ip, range(start_port, end_port + 1))
            except ValueError:
                print("Insira apenas números válidos.")
        elif opcao == "2":
            list_active_connections()
        elif opcao == "3":
            parse_logs()
        elif opcao == "4":
            export_data()
        elif opcao == "5":
            print("A sair...")
            break
        else:
            print("Opção inválida!")

menu()
```
