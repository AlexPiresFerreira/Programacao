## Objetivo

O **Git Large File Storage (Git LFS)** permite versionar arquivos grandes, como PDFs, vídeos, imagens, modelos e arquivos compactados, sem armazenar diretamente todo o conteúdo binário no histórico normal do Git.

---

## 1. Pré-requisitos

Verifique se o Git está instalado:

```powershell
git --version
```

Verifique se o Git LFS está instalado:

```powershell
git lfs version
```

Se ainda não estiver instalado no Windows, pode ser utilizado:

```powershell
winget install GitHub.GitLFS
ou 
https://git-lfs.com/
```

---

## 2. Inicializar o Git LFS

A inicialização deve ser feita apenas uma vez por usuário:

```powershell
git lfs install
```

Resultado esperado:

```text
Git LFS initialized.
```

Esse comando configura o Git LFS no ambiente local e instala os hooks necessários.

---

## 3. Acessar a pasta do repositório

Entre na pasta local do repositório Git:

```powershell
cd "C:\caminho\do\repositorio"
```

---
## 4. Configurar arquivos para o Git LFS

Para rastrear todos os arquivos PDF:

```powershell
git lfs track "*.pdf"
```

Esse comando cria ou atualiza o arquivo:

```text
.gitattributes
```

O arquivo `.gitattributes` informa ao Git quais arquivos devem ser gerenciados pelo Git LFS.

---

## 5. Verificar a configuração

No PowerShell, visualize o conteúdo do arquivo `.gitattributes` com:

```powershell
Get-Content .gitattributes
```

Também é possível visualizar as regras configuradas:

```powershell
git lfs track
```

---

## 6. Adicionar o arquivo e a configuração

Adicione o arquivo `.gitattributes`:

```powershell
git add .gitattributes
```

Adicione o arquivo grande:

```powershell
git add "CEHExamBlueprintv5.pdf"
```

Confira o que será enviado:

```powershell
git status
```

---

## 7. Criar o commit

Crie um commit contendo a configuração e o arquivo:

```powershell
git commit -m "Adiciona blueprint CEH usando Git LFS"
```

Se o Git solicitar uma identidade, configure seu nome e e-mail:

```powershell
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@example.com"
```

---

## 8. Conectar ao repositório do GitHub

Se ainda não houver um repositório remoto configurado, adicione o endereço do GitHub:

```powershell
git remote add origin https://github.com/USUARIO/REPOSITORIO.git
```

Verifique o endereço configurado:

```powershell
git remote -v
```

Caso o branch principal seja chamado `master`, altere-o para `main`:

```powershell
git branch -M main
```

---

## 9. Enviar o arquivo para o GitHub

Envie o commit e o arquivo gerenciado pelo Git LFS:

```powershell
git push -u origin main
```

Durante o processo, o Git enviará:

- Um pequeno arquivo de ponteiro para o repositório Git.
- O arquivo original para o armazenamento do Git LFS.

---

## 10. Confirmar se o arquivo está sendo gerenciado pelo LFS

Liste os arquivos rastreados pelo Git LFS:

```powershell
git lfs ls-files
```

O arquivo deverá aparecer na lista:

```text
CEHExamBlueprintv5.pdf
```

Verifique o status do Git LFS:

```powershell
git lfs status
```

Para verificar os atributos aplicados ao arquivo:

```powershell
git check-attr -a -- "CEHExamBlueprintv5.pdf"
```

---

## Fluxo completo resumido

Execute os comandos a partir da pasta do repositório:

```powershell
git lfs install
git lfs track "CEHExamBlueprintv5.pdf"
git add .gitattributes
git add "CEHExamBlueprintv5.pdf"
git commit -m "Adiciona blueprint CEH usando Git LFS"
git branch -M main
git push -u origin main
```

---
## Caso o arquivo já tenha sido enviado sem Git LFS

Se o arquivo grande já foi commitado anteriormente sem o Git LFS, apenas executar `git lfs track` não corrige o histórico antigo.

Para migrar arquivos PDF existentes no histórico:

```powershell
git lfs migrate import --include="*.pdf"
```

Depois, envie o histórico atualizado:

```powershell
git push --force-with-lease origin main
```

> **Atenção:** esse procedimento reescreve o histórico do repositório. Evite utilizá-lo em repositórios compartilhados sem avisar os demais colaboradores.

---

## Clonar um repositório que utiliza Git LFS

Depois de instalar o Git LFS:

```powershell
git lfs install
```

Clone o repositório normalmente:

```powershell
git clone https://github.com/USUARIO/REPOSITORIO.git
```

Se o repositório já tiver sido clonado e os arquivos reais ainda não tiverem sido baixados:

```powershell
git lfs pull
```

---

## Baixar apenas os ponteiros dos arquivos

Para evitar o download imediato dos arquivos grandes:

```powershell
$env:GIT_LFS_SKIP_SMUDGE = "1"
git clone https://github.com/USUARIO/REPOSITORIO.git
```

Para baixar os arquivos posteriormente:

```powershell
git lfs pull
```

---

## Comandos úteis

| Comando | Função |
|---|---|
| `git lfs install` | Inicializa o Git LFS |
| `git lfs track "*.pdf"` | Rastreia todos os arquivos PDF |
| `git lfs track "arquivo.pdf"` | Rastreia um arquivo específico |
| `git lfs track` | Lista os padrões configurados |
| `git lfs ls-files` | Lista os arquivos controlados pelo LFS |
| `git lfs status` | Exibe o status dos arquivos LFS |
| `git lfs pull` | Baixa os arquivos LFS |
| `git lfs fetch` | Busca objetos LFS sem atualizar os arquivos de trabalho |
| `git lfs migrate import` | Migra arquivos existentes para o LFS |
| `git lfs prune` | Remove objetos LFS locais não utilizados |

---

## Estrutura esperada do repositório

Depois da configuração, a estrutura poderá ser semelhante a:

```text
meu-repositorio/
├── .git/
├── .gitattributes
└── CEHExamBlueprintv5.pdf
```

O arquivo `.gitattributes` deve permanecer no repositório, pois ele contém as regras que informam ao Git quais arquivos usam Git LFS.

---
