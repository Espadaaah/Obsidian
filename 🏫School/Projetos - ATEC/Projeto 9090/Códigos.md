


# Main.py
---
```python
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

## Scan_ports.py
---
```python
import socket

def scan_ports(ip, ports):

    print(f"\n[+] A iniciar scan de ports em {ip} no intervalo {ports.start}-{ports.stop - 1}...\n")

    open_ports = []

  

    for port in ports:

        with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:

            s.settimeout(0.5)

            result = s.connect_ex((ip, port))

            if result == 0:

                print(f"[ABERTA] Port {port}")

                open_ports.append(port)

  

    if not open_ports:

        print("Nenhuma port aberta.")

    return open_ports
```

# Active_connections.py
---
```python
import psutil

def list_active_connections():

    print("\n[+] Conexões de rede ativas:\n")

  

    connections = psutil.net_connections(kind='inet')

  

    for conn in connections:

        laddr = f"{conn.laddr.ip}:{conn.laddr.port}" if conn.laddr else ""

        raddr = f"{conn.raddr.ip}:{conn.raddr.port}" if conn.raddr else ""

        print(f"{conn.type} | {conn.status} | Local: {laddr} | Remoto: {raddr}")
```

# Log_parser.py
---
```python
import os

import platform

import re

  

from db_handler import save_log_entry

from geoip_utils import get_country_by_ip

  

def parse_logs():

    system = platform.system()

  

    print("\n[+] Análise de Logs")

    print("1. Análise automática (logs padrão do sistema)")

    print("2. Fornecer caminho manual para o ficheiro de log")

  

    escolha = input("Escolha uma opção (1 ou 2): ").strip()

  

    if system == "Linux":

        if escolha == "1":

            paths = {

                "ssh": "/var/log/auth.log",

                "http": "/var/log/apache2/access.log"

            }

            for servico, caminho in paths.items():

                analisar_log_linux(caminho, servico)

        elif escolha == "2":

            caminho = input("Insira o caminho completo do ficheiro de log: ").strip()

            servico = input("Indique o nome do serviço (ex: ssh, http): ").strip().lower()

            analisar_log_linux(caminho, servico)

        else:

            print("Opção inválida.")

    elif system == "Windows":

        try:

            import win32evtlog

            import win32evtlogutil

  

            if escolha == "1":

                analisar_log_windows_automatico()

            elif escolha == "2":

                print("No Windows apenas é suportada leitura do Event Log (modo automático).")

            else:

                print("Opção inválida.")

        except ImportError:

            print("Módulo 'pywin32' não instalado. Execute: pip install pywin32")

    else:

        print("Sistema operativo não suportado.")

  

def analisar_log_linux(caminho, servico):

    if not os.path.exists(caminho):

        print(f"[!] Caminho inválido: {caminho}")

        return

  

    print(f"\n[+] A ler log: {caminho} ({servico.upper()})")

  

    with open(caminho, "r", encoding='utf-8', errors='ignore') as f:

        for linha in f:

            if "Failed password" in linha or "GET /" in linha:

                ip_match = re.search(r'(\d+\.\d+\.\d+\.\d+)', linha)

                data = ' '.join(linha.split()[:3])

                if ip_match:

                    ip = ip_match.group(1)

                    pais = get_country_by_ip(ip)

                    print(f"{servico.upper()} | {ip} | {pais} | {data}")

                    save_log_entry(servico, ip, pais, data)

  

def analisar_log_windows_automatico():

    import win32evtlog

    import win32evtlogutil

  

    server = 'localhost'

    log_type = 'Security'

  

    try:

        handle = win32evtlog.OpenEventLog(server, log_type)

        total = win32evtlog.GetNumberOfEventLogRecords(handle)

  

        print(f"\n[+] A analisar {total} entradas do log de segurança do Windows...\n")

  

        events = win32evtlog.ReadEventLog(handle,

            win32evtlog.EVENTLOG_BACKWARDS_READ | win32evtlog.EVENTLOG_SEQUENTIAL_READ,

            0)

  

        for event in events:

            if event.EventID in [4625, 4624]:  # Login failed/success

                message = win32evtlogutil.SafeFormatMessage(event, log_type)

                ip_match = re.search(r'(\d+\.\d+\.\d+\.\d+)', message)

                data = event.TimeGenerated.Format()

                servico = "login"

  

                if ip_match:

                    ip = ip_match.group(1)

                    pais = get_country_by_ip(ip)

                    print(f"{servico.upper()} | {ip} | {pais} | {data}")

                    save_log_entry(servico, ip, pais, data)

    except Exception as e:

        print(f"[ERRO] {e}")
```

# Export_utils.py
---
```python
from db_handler import get_all_logs

import csv

  

def export_data():

    logs = get_all_logs()

  

    if not logs:

        print("Nenhum dado para exportar.")

        return

  

    formato = input("Escolha o formato (txt/csv): ").strip().lower()

  

    if formato == "txt":

        with open("export_logs.txt", "w") as f:

            for log in logs:

                f.write(f"{log[0]} | {log[1]} | {log[2]} | {log[3]}\n")

        print("Exportado para export_logs.txt")

  

    elif formato == "csv":

        with open("export_logs.csv", "w", newline='') as f:

            writer = csv.writer(f)

            writer.writerow(["Serviço", "IP", "País", "Data"])

            writer.writerows(logs)

        print("Exportado para export_logs.csv")

    else:

        print("Formato inválido.")
```

# Geoip_utils.py
---
```python
import requests

  

def get_country_by_ip(ip):

    try:

        response = requests.get(f"https://ipapi.co/{ip}/country_name/", timeout=3)

        return response.text.strip()

    except Exception:

        return "Desconhecido"
```

# Db_handler.py
---
```python
import sqlite3

import os

  

DB_FILE = "logs.db"

  

def initialize_db():

    conn = sqlite3.connect(DB_FILE)

    c = conn.cursor()

  

    c.execute('''

        CREATE TABLE IF NOT EXISTS logs (

            id INTEGER PRIMARY KEY AUTOINCREMENT,

            service TEXT,

            ip TEXT,

            country TEXT,

            date TEXT

        )

    ''')

  

    conn.commit()

    conn.close()

  

def save_log_entry(service, ip, country, date):

    conn = sqlite3.connect(DB_FILE)

    c = conn.cursor()

    c.execute("INSERT INTO logs (service, ip, country, date) VALUES (?, ?, ?, ?)",

              (service, ip, country, date))

    conn.commit()

    conn.close()

  

def get_all_logs():

    conn = sqlite3.connect(DB_FILE)

    c = conn.cursor()

    c.execute("SELECT service, ip, country, date FROM logs")

    rows = c.fetchall()

    conn.close()

    return rows
```
