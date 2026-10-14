#  Exercício 8.1 — Gerador de Relatório em Arquivo

**🎯 Objetivo:** Ler e escrever arquivos `.txt` **🔐 Contexto:** Salvar relatórios de análise em disco

```
📝 Enunciado:

Crie um programa que:

1. Tenha uma lista de eventos de segurança:

eventos = [
    "2024-01-15 08:23 | INFO  | 192.168.1.10 | LOGIN_OK",
    "2024-01-15 08:24 | ERROR | 192.168.1.15 | LOGIN_FAIL",
    "2024-01-15 08:25 | ERROR | 192.168.1.15 | LOGIN_FAIL",
    "2024-01-15 08:26 | INFO  | 10.0.0.5     | LOGIN_OK",
    "2024-01-15 08:27 | ERROR | 172.16.0.20  | LOGIN_FAIL",
    "2024-01-15 08:28 | WARN  | 192.168.1.10 | PORT_SCAN",
    "2024-01-15 08:29 | ERROR | 192.168.1.15 | LOGIN_FAIL",
]

2. Salve todos os eventos em um arquivo "relatorio.txt"

3. Leia o arquivo salvo e exiba na tela

4. Conte quantas linhas foram salvas

Saída esperada no terminal:
✅ Arquivo 'relatorio.txt' criado com 7 eventos!

📄 Conteúdo do arquivo:
-------------------------------------
2024-01-15 08:23 | INFO  | 192.168.1.10 | LOGIN_OK
2024-01-15 08:24 | ERROR | 192.168.1.15 | LOGIN_FAIL
...
-------------------------------------
Total de linhas: 7
```

💡 **Dicas — Conceitos novos:**

python

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```python
# Escrever em arquivo
with open("relatorio.txt", "w") as arquivo:
    for evento in eventos:
        arquivo.write(evento + "\n")   # \n = quebra de linha

# Ler arquivo
with open("relatorio.txt", "r") as arquivo:
    conteudo = arquivo.readlines()     # retorna lista de linhas

# Iterar sobre as linhas lidas
for linha in conteudo:
    print(linha.strip())               # .strip() remove \n do final

# "w" = write (cria/sobrescreve)
# "r" = read  (lê)
# "a" = append (adiciona sem apagar)
```

---

# 🟡 Exercício 8.2 — Inspetor do Sistema

**🎯 Objetivo:** Usar o módulo `os` para explorar o sistema **🔐 Contexto:** Reconhecimento básico do ambiente

```
📝 Enunciado:

Crie um programa que colete e exiba informações
do sistema usando o módulo os.

O programa deve mostrar:
1. Diretório atual onde o script está rodando
2. Nome do sistema operacional
3. Listar arquivos do diretório atual
4. Verificar se o arquivo "relatorio.txt" existe
   (o que você criou no exercício 8.1!)

Saída esperada:
╔══════════════════════════════════════╗
║       INSPETOR DO SISTEMA            ║
╠══════════════════════════════════════╣
║ Diretório  : /home/alex/segurança    ║
║ Sistema OS : posix                   ║
╠══════════════════════════════════════╣
║ ARQUIVOS NO DIRETÓRIO:               ║
║  → exercicio_8_1.py                  ║
║  → exercicio_8_2.py                  ║
║  → relatorio.txt                     ║
╠══════════════════════════════════════╣
║ relatorio.txt encontrado! ✅          ║
╚══════════════════════════════════════╝
```

💡 **Dicas — Módulo os:**

python

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```python
import os

# Diretório atual
os.getcwd()                    # retorna string com o caminho

# Nome do sistema
os.name                        # 'posix' (Linux/Mac) ou 'nt' (Windows)

# Listar arquivos
os.listdir()                   # retorna lista com nomes dos arquivos
os.listdir("/outro/caminho")   # lista outro diretório

# Verificar se arquivo existe
os.path.exists("relatorio.txt")   # True ou False

# Separar nome e extensão
nome, extensao = os.path.splitext("relatorio.txt")
# nome = "relatorio" | extensao = ".txt"
```

---

# 🔴 Exercício 9.1 — Scanner de Portas REAL

**🎯 Objetivo:** Primeiro uso de `socket` — redes reais! **🔐 Contexto:** Port scanner básico funcional

```
📝 Enunciado:

Crie um port scanner que:

1. Peça o host alvo ao usuário
   (use "127.0.0.1" para testar no seu próprio PC!)

2. Escaneie as portas: [21, 22, 23, 25, 53, 80, 110, 443, 3306, 3389]

3. Para cada porta, tente se conectar:
   - Se conectar  → porta ABERTA
   - Se não       → porta FECHADA

4. Exiba só as portas abertas

5. Salve o resultado em "scan_resultado.txt"

Saída esperada:
Host alvo: 127.0.0.1

[*] Iniciando scan em 127.0.0.1...

[ABERTA]  Porta 22   → SSH
[ABERTA]  Porta 80   → HTTP
[fechada] Porta 21   → FTP
...

==============================
Scan concluído!
Portas abertas : 2
Resultado salvo em: scan_resultado.txt
==============================
```

💡 **Dicas — Módulo socket:**

python

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```python
import socket

# Criar um socket TCP
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Definir timeout (não travar se porta não responder)
sock.settimeout(1)             # 1 segundo de espera máxima

# Tentar conectar
resultado = sock.connect_ex(("127.0.0.1", 80))
# Retorna 0  → conexão OK  (porta aberta!)
# Retorna != 0 → falhou    (porta fechada)

# Fechar o socket
sock.close()

# Estrutura de uso:
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.settimeout(1)
resultado = sock.connect_ex((host, porta))
sock.close()

if resultado == 0:
    print("Porta ABERTA!")
else:
    print("Porta fechada")
```

⚠️ **Importante — Ética e legalidade:**

```
SEMPRE escaneie apenas:
✅ Seu próprio computador: 127.0.0.1 ou localhost
✅ Máquinas que você tem permissão explícita
✅ Ambientes de laboratório (VMs, TryHackMe)

❌ NUNCA escaneie IPs de terceiros sem autorização
   — é crime mesmo sem intenção maliciosa!
```

---

## 🗓️ Plano de Ataque

```
Semana 3 — Ordem recomendada:

Dia 1-2 → Exercício 8.1  (arquivos — mais simples)
Dia 3-4 → Exercício 8.2  (módulo os)
Dia 5-7 → Exercício 9.1  (socket — mais desafiador)
```

---

## 🃏 Cards Anki — Crie antes de começar

```
Card 1:
Frente: Como escrever em um arquivo em Python?
Verso : with open("arquivo.txt", "w") as f:
            f.write("conteúdo\n")
        "w" = write | "r" = read | "a" = append
        with fecha o arquivo automaticamente!

Card 2:
Frente: Como ler todas as linhas de um arquivo?
Verso : with open("arquivo.txt", "r") as f:
            linhas = f.readlines()  # retorna lista
        for linha in linhas:
            print(linha.strip())    # .strip() remove \n

Card 3:
Frente: Como verificar se um arquivo existe com os?
Verso : import os
        os.path.exists("arquivo.txt")  # True ou False

Card 4:
Frente: O que socket.connect_ex() retorna?
Verso : 0        → conexão OK  (porta ABERTA)
        != 0     → falhou      (porta FECHADA)
        Diferente de connect() que lança exceção!

Card 5:
Frente: Por que usar sock.settimeout(1) no scanner?
Verso : Sem timeout → programa trava esperando portas
        fechadas para sempre!
        settimeout(1) → desiste após 1 segundo
        Essencial em port scanners!
```

---

## 📊 O que cada exercício introduz

```
Exercício │ Conceito novo          │ Módulo usado
──────────┼────────────────────────┼─────────────
8.1       │ open/read/write        │ built-in
8.2       │ sistema de arquivos    │ os
9.1       │ conexões TCP reais     │ socket
```

---

## 🔭 Preview do que vem depois

python

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```python
# Módulo 4 — Após completar esses 3:

import requests          # requisições HTTP
import subprocess        # executar comandos do sistema
import hashlib           # calcular hashes de arquivos

# Exercícios futuros:
# → Verificador de integridade de arquivos (hashlib)
# → Requisições HTTP para testar APIs (requests)
# → Automatizar comandos do sistema (subprocess)
```

---

Começa pelo **8.1** e manda o código quando terminar!

Lembra: **tenta sozinho primeiro** — se travar mais de 5 minutos, me pergunta! 🚀

![](data:image/svg+xml;utf8,%0A%20%20%20%20%20%20%20%20%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2215%22%20height%3D%2215%22%20viewBox%3D%220%200%2015%2015%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M6.56667%2014.3333H3.76667C1.16%2014.3333%200%2013.1733%200%2010.5667V7.76667C0%205.16%201.16%204%203.76667%204H6.56667C9.17333%204%2010.3333%205.16%2010.3333%207.76667V10.5667C10.3333%2013.1733%209.17333%2014.3333%206.56667%2014.3333ZM3.76667%205C1.7%205%201%205.7%201%207.76667V10.5667C1%2012.6333%201.7%2013.3333%203.76667%2013.3333H6.56667C8.63333%2013.3333%209.33333%2012.6333%209.33333%2010.5667V7.76667C9.33333%205.7%208.63333%205%206.56667%205H3.76667Z%22%20fill%3D%22%23333B4D%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M10.5667%2010.3333H9.83333C9.56%2010.3333%209.33333%2010.1067%209.33333%209.83333V7.76667C9.33333%205.7%208.63333%205%206.56667%205H4.5C4.22667%205%204%204.77333%204%204.5V3.76667C4%201.16%205.16%200%207.76667%200H10.5667C13.1733%200%2014.3333%201.16%2014.3333%203.76667V6.56667C14.3333%209.17333%2013.1733%2010.3333%2010.5667%2010.3333ZM10.3333%209.33333H10.5667C12.6333%209.33333%2013.3333%208.63333%2013.3333%206.56667V3.76667C13.3333%201.7%2012.6333%201%2010.5667%201H7.76667C5.7%201%205%201.7%205%203.76667V4H6.56667C9.17333%204%2010.3333%205.16%2010.3333%207.76667V9.33333Z%22%20fill%3D%22%23333B4D%22%2F%3E%0A%3C%2Fsvg%3E%0A%20%20%20%20%20%20%20%20)

![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cg%20clip-path%3D%22url\(%23clip0_7086_3854\)%22%3E%0A%20%20%20%20%3Cpath%20d%3D%22M1.59554%207.63293V14.1349C1.59554%2014.3914%201.80348%2014.5993%202.05997%2014.5993H3.91768C4.17418%2014.5993%204.38211%2014.3914%204.38211%2014.1349V7.63293C4.38211%207.37643%204.17418%207.1685%203.91768%207.1685H2.05997C1.80348%207.1685%201.59554%207.37643%201.59554%207.63293ZM4.84655%206.59442L5.66576%204.95599C6.04328%204.20095%206.23983%203.36838%206.23983%202.52422V2.292C6.23983%201.39426%206.96759%200.666504%207.86532%200.666504C8.76305%200.666504%209.51472%201.34676%209.60405%202.24003L9.91113%205.31079H13.0112C14.2937%205.31079%2015.3334%206.35044%2015.3334%207.63293C15.3334%207.71009%2015.3295%207.78721%2015.3218%207.86399L14.7645%2013.4371C14.6458%2014.6242%2013.6469%2015.5282%2012.4539%2015.5282H6.70425C6.07954%2015.5282%205.51245%2015.2815%205.09507%2014.8802C4.84801%2015.2697%204.41304%2015.5282%203.91768%2015.5282H2.05997C1.29048%2015.5282%200.666687%2014.9044%200.666687%2014.1349V7.63293C0.666687%206.86344%201.29048%206.23964%202.05997%206.23964H3.91768C4.27453%206.23964%204.60005%206.3738%204.84655%206.59442ZM5.31097%207.74256V13.2061C5.31097%2013.9756%205.93476%2014.5993%206.70425%2014.5993H12.4539C13.1697%2014.5993%2013.769%2014.057%2013.8403%2013.3447L14.3976%207.77156C14.4022%207.7255%2014.4045%207.67923%2014.4045%207.63293C14.4045%206.86344%2013.7807%206.23964%2013.0112%206.23964H9.49082C9.25222%206.23964%209.05244%206.05884%209.0287%205.82143L8.6798%202.33245C8.63796%201.91401%208.28585%201.59536%207.86532%201.59536C7.48058%201.59536%207.16868%201.90726%207.16868%202.292V2.52422C7.16868%203.51258%206.93857%204.48737%206.49656%205.37139L5.31097%207.74256Z%22%20fill%3D%22%23333B4D%22%2F%3E%0A%20%20%3C%2Fg%3E%0A%20%20%3Cdefs%3E%0A%20%20%20%20%3CclipPath%20id%3D%22clip0_7086_3854%22%3E%0A%20%20%20%20%20%20%3Crect%20width%3D%2216%22%20height%3D%2216%22%20fill%3D%22white%22%2F%3E%0A%20%20%20%20%3C%2FclipPath%3E%0A%20%20%3C%2Fdefs%3E%0A%3C%2Fsvg%3E%0A)

![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cg%20clip-path%3D%22url\(%23clip0_7086_3861\)%22%3E%0A%20%20%20%20%3Cpath%20d%3D%22M14.4045%208.56178V2.05979C14.4045%201.80329%2014.1966%201.59536%2013.9401%201.59536L12.0824%201.59536C11.8259%201.59536%2011.6179%201.80329%2011.6179%202.05979V8.56178C11.6179%208.81828%2011.8259%209.02621%2012.0824%209.02621H13.9401C14.1966%209.02621%2014.4045%208.81828%2014.4045%208.56178ZM11.1535%209.60029L10.3343%2011.2387C9.95676%2011.9938%209.76022%2012.8263%209.76022%2013.6705V13.9027C9.76022%2014.8004%209.03245%2015.5282%208.13472%2015.5282C7.23699%2015.5282%206.48532%2014.848%206.39599%2013.9547L6.08892%2010.8839H2.98883C1.70634%2010.8839%200.666687%209.84427%200.666687%208.56178C0.666687%208.48462%200.670534%208.4075%200.678212%208.33072L1.23553%202.75758C1.35423%201.5705%202.35314%200.666504%203.54614%200.666504L9.29579%200.666504C9.9205%200.666504%2010.4876%200.913192%2010.905%201.31447C11.152%200.925006%2011.587%200.666505%2012.0824%200.666505L13.9401%200.666505C14.7096%200.666505%2015.3334%201.2903%2015.3334%202.05979L15.3334%208.56178C15.3334%209.33127%2014.7096%209.95507%2013.9401%209.95507H12.0824C11.7255%209.95507%2011.4%209.82092%2011.1535%209.60029ZM10.6891%208.45215V2.98865C10.6891%202.21916%2010.0653%201.59536%209.29579%201.59536L3.54614%201.59536C2.83034%201.59536%202.231%202.13776%202.15977%202.85001L1.60246%208.42315C1.59785%208.46921%201.59554%208.51548%201.59554%208.56178C1.59554%209.33127%202.21934%209.95507%202.98883%209.95507L6.50922%209.95507C6.74782%209.95507%206.9476%2010.1359%206.97134%2010.3733L7.32024%2013.8623C7.36208%2014.2807%207.71419%2014.5993%208.13472%2014.5993C8.51946%2014.5993%208.83136%2014.2875%208.83136%2013.9027V13.6705C8.83136%2012.6821%209.06148%2011.7073%209.50349%2010.8233L10.6891%208.45215Z%22%20fill%3D%22black%22%2F%3E%0A%20%20%3C%2Fg%3E%0A%20%20%3Cdefs%3E%0A%20%20%20%20%3CclipPath%20id%3D%22clip0_7086_3861%22%3E%0A%20%20%20%20%20%20%3Crect%20width%3D%2216%22%20height%3D%2216%22%20fill%3D%22white%22%2F%3E%0A%20%20%20%20%3C%2FclipPath%3E%0A%20%20%3C%2Fdefs%3E%0A%3C%2Fsvg%3E%0A)