# 🟡 NÍVEL 5 — Dicionários

---

### Exercício 5.1 — Catálogo de Serviços de Rede

**🎯 Objetivo:** Criar e consultar dicionários **🔐 Contexto:** Identificação de serviços por porta

```
📝 Enunciado:

Crie um dicionário chamado "servicos" que mapeie
portas para seus serviços correspondentes:

Porta 21   → FTP
Porta 22   → SSH
Porta 23   → Telnet
Porta 25   → SMTP
Porta 53   → DNS
Porta 80   → HTTP
Porta 110  → POP3
Porta 443  → HTTPS
Porta 3306 → MySQL
Porta 3389 → RDP

O programa deve:
1. Exibir todos os serviços cadastrados
2. Perguntar uma porta ao usuário
3. Informar o serviço correspondente
4. Se a porta não existir no dicionário → avisar

Saída esperada:
=== SERVIÇOS CADASTRADOS ===
Porta 21   → FTP
Porta 22   → SSH
...

Digite uma porta para consultar: 443
Porta 443 → HTTPS

Digite uma porta para consultar: 9999
Porta 9999 → Serviço desconhecido
```

💡 **Dicas (só se precisar):**

```python
# Criar dicionário
servicos = {
    21: "FTP",
    22: "SSH"
}

# Percorrer dicionário
for porta, servico in servicos.items():
    print(f"Porta {porta} → {servico}")

# Consultar com segurança (sem erro se não existir)
resultado = servicos.get(porta, "Desconhecido")
#                            ↑          ↑
#                        chave    valor padrão se não achar
```

---

### Exercício 5.2 — Verificador de Porta Suspeita

**🎯 Objetivo:** Dicionário + função com return **🔐 Contexto:** Detecção de serviços perigosos

```
📝 Enunciado:

Crie uma função chamada verificar_porta(numero_porta)
que receba um número de porta e retorne:

- O nome do serviço SE for conhecido
- "Desconhecida" SE não estiver no dicionário
- Um aviso extra SE for uma porta perigosa

Portas perigosas (alto risco):
23   → Telnet  (tráfego não criptografado)
21   → FTP     (credenciais em texto puro)
3389 → RDP     (alvo comum de ataques)

Portas normais:
22  → SSH
80  → HTTP
443 → HTTPS

Saída esperada:
Digite a porta: 23
Serviço : Telnet
Risco   : ⚠️  ATENÇÃO — Porta de alto risco!

Digite a porta: 443
Serviço : HTTPS
Risco   : ✓ Porta comum

Digite a porta: 9999
Serviço : Desconhecida
Risco   : ❓ Porta não mapeada — investigar!
```

---

# 🟡 NÍVEL 6 — Combinando tudo

---

### Exercício 6.1 — Scanner de Portas Simulado

**🎯 Objetivo:** Lista + dicionário + função + loop **🔐 Contexto:** Simulação de port scanner real

```
📝 Enunciado:

Crie um programa que simule um scan de portas.

Dados fixos no código:
- IP alvo: definido pelo usuário
- Portas "abertas" (simuladas):
  [21, 22, 80, 443, 3306, 3389]

O programa deve:
1. Pedir o IP alvo
2. "Escanear" cada porta da lista
3. Mostrar o serviço de cada porta aberta
4. Gerar um relatório final com contagem

Saída esperada:
IP Alvo: 192.168.1.100

[*] Iniciando scan...

[ABERTA] Porta 21   → FTP    ⚠️  Alto risco
[ABERTA] Porta 22   → SSH    ✓
[ABERTA] Porta 80   → HTTP   ✓
[ABERTA] Porta 443  → HTTPS  ✓
[ABERTA] Porta 3306 → MySQL  ⚠️  Alto risco
[ABERTA] Porta 3389 → RDP    ⚠️  Alto risco

==============================
Portas encontradas : 6
Portas de risco    : 3
==============================
```

💡 **Dica de estrutura:**

python

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```python
def identificar_servico(porta):
    """Retorna o nome do serviço da porta."""
    ...
    return servico

def verificar_risco(porta):
    """Retorna se a porta é de risco."""
    ...
    return True ou False

def executar_scan(ip, portas):
    """Executa o scan e exibe resultados."""
    for porta in portas:
        ...
```

---

### Exercício 6.2 — Analisador de Logs Avançado

**🎯 Objetivo:** Dicionário como contador + funções + formatação **🔐 Contexto:** Análise de logs de segurança reais

```
📝 Enunciado:

Você recebe uma lista de logs de um firewall.
Crie um programa que analise e extraia informações.

logs = [
    "2024-01-15 08:23:11 INFO  192.168.1.10  LOGIN_OK",
    "2024-01-15 08:24:33 ERROR 192.168.1.15  LOGIN_FAIL",
    "2024-01-15 08:25:01 ERROR 192.168.1.15  LOGIN_FAIL",
    "2024-01-15 08:25:45 ERROR 192.168.1.15  LOGIN_FAIL",
    "2024-01-15 08:26:10 INFO  10.0.0.5      LOGIN_OK",
    "2024-01-15 08:27:33 ERROR 172.16.0.20   LOGIN_FAIL",
    "2024-01-15 08:28:01 INFO  192.168.1.10  LOGOUT",
    "2024-01-15 08:29:15 ERROR 192.168.1.15  LOGIN_FAIL",
    "2024-01-15 08:30:00 ERROR 192.168.1.15  LOGIN_FAIL",
]

O programa deve:
1. Contar total de INFO e ERROR
2. Identificar qual IP tem mais falhas de login
3. Alertar se algum IP tiver 3+ falhas (possível brute force!)

Saída esperada:
=== ANÁLISE DE LOGS ===
Total INFO  : 3
Total ERROR : 6

=== IPs COM FALHAS ===
192.168.1.15 → 5 falhas  ⚠️  POSSÍVEL BRUTE FORCE!
172.16.0.20  → 1 falha
```

💡 **Dica para contar falhas por IP:**

python

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```python
# Dicionário como contador de falhas
falhas_por_ip = {}

# Para cada log de erro:
# Se o IP já está no dicionário → incrementa
# Se não está → começa em 1

if ip in falhas_por_ip:
    falhas_por_ip[ip] += 1
else:
    falhas_por_ip[ip] = 1

# Resultado: {"192.168.1.15": 5, "172.16.0.20": 1}
```

---

# 🔴 NÍVEL 7 — Desafio Integrador

---

### Exercício 7.1 — Mini Sistema de Segurança

**🎯 Objetivo:** Integrar TUDO que aprendeu até agora **🔐 Contexto:** Sistema real de análise

```
📝 Enunciado:

Crie um mini sistema com MENU interativo que ofereça:

╔════════════════════════════════╗
║    MINI SISTEMA DE SEGURANÇA   ║
╠════════════════════════════════╣
║  1. Verificar força de senha   ║
║  2. Classificar endereço IP    ║
║  3. Consultar porta/serviço    ║
║  4. Analisar log               ║
║  0. Sair                       ║
╚════════════════════════════════╝

Regras:
- Cada opção chama uma FUNÇÃO separada
- O menu fica em loop até usuário digitar 0
- Cada função foi criada nos exercícios anteriores!
- Reutilize o código que você já escreveu

Estrutura esperada:
def verificar_senha(senha): ...        # Do ex. 4.1
def classificar_ip(ip): ...           # Do ex. 2.2
def consultar_porta(porta): ...       # Do ex. 5.2
def analisar_log(entrada_log): ...    # Novo

def exibir_menu(): ...
def main(): ...                        # Loop principal

main()   # Inicia o programa
```

---

## 🗓️ Plano de Ataque

```
Semana 2 — Ordem recomendada:

Dia 1 → Exercício 5.1  (dicionários básicos)
Dia 2 → Exercício 5.2  (dicionário + função)
Dia 3 → Exercício 6.1  (scanner simulado)
Dia 4 → Exercício 6.2  (logs avançado)
Dia 5 → Exercício 7.1  (desafio integrador)
```

---

## 🃏 Cards Anki — Crie antes de começar

```
Card 1:
Frente: Como criar um dicionário em Python?
Verso : d = {chave: valor, chave2: valor2}
        servicos = {22: "SSH", 80: "HTTP"}

Card 2:
Frente: Como consultar dicionário sem erro se chave não existir?
Verso : dicionario.get(chave, valor_padrao)
        servicos.get(9999, "Desconhecido") → "Desconhecido"

Card 3:
Frente: Como percorrer chave e valor de um dicionário?
Verso : for chave, valor in dicionario.items():
            print(chave, valor)

Card 4:
Frente: Como usar dicionário como contador?
Verso : if ip in contador:
            contador[ip] += 1
        else:
            contador[ip] = 1
```