# Minicurso SDD

Documentação do Minicurso de SDD — desde a instalação das ferramentas até os inputs para recriar os projetos apresentados.

---

## Passo a passo: Instalação das Ferramentas

### 1. Git

Escolha o comando conforme seu sistema operacional:

| Sistema | Comando |
|---------|---------|
| Windows | `winget install --id Git.Git -e --source winget` |
| Ubuntu / Debian / Linux Mint / Pop!_OS | `sudo apt update && sudo apt install git -y` |
| Fedora | `sudo dnf install git -y` |
| Arch Linux / Manjaro | `sudo pacman -S git --noconfirm` |
| Red Hat (RHEL) / CentOS | `sudo yum install git -y` |
| macOS | `xcode-select --install` (já inclui Git) |

---

### 2. UV (gerenciador de projetos Python)

#### Windows
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

#### Linux / macOS
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

---

### 3. SpecKit (Spec-CLI do GitHub)

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git@v0.12.4
```

> **Nota:** Se apresentar erro, provavelmente é porque o UV não está instalado. Volte ao passo 2.

---

### 4. Node.js (necessário para o opencode via npm)

#### Windows
Baixe o instalador em [nodejs.org](https://nodejs.org) ou use:
```powershell
winget install OpenJS.NodeJS.LTS
```

#### Linux / macOS
```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs
```

---

### 5. Opencode (CLI de IA para programação)

#### Windows (via npm)
```bash
npm i -g opencode-ai
```

#### Linux / macOS (via script oficial)
```bash
curl -fsSL https://opencode.ai/install | bash
```

> **Nota:** O Windows requer o Node.js instalado (passo 4). No Linux/macOS o script oficial instala as dependências automaticamente.

---

## Verificação da Instalação

Após instalar tudo, confirme que as ferramentas estão disponíveis:

```bash
git --version
uv --version
specify --version
opencode --version
```

---

## Como usar as ferramentas

### Visão geral do SDD (Spec-Driven Development)

O SDD inverte a abordagem tradicional: primeiro você escreve **especificações** do que quer construir (o *quê* e o *porquê*), e o agente de IA gera o código a partir delas. As especificações viram o guia do projeto — não são descartadas depois.

### Fluxo de trabalho SDD

O ciclo SDD tem 8 etapas. Todas são executadas **dentro do agente de IA** (Opencode) usando comandos `/speckit.*`:

| Etapa | O que faz |
|-------|-----------|
| 1. `/speckit.constitution` | Define as regras e princípios do projeto |
| 2. `/speckit.specify` | Descreve o que você quer construir |
| 3. `/speckit.clarify` | Tira dúvidas sobre a especificação |
| 4. `/speckit.plan` | Cria o plano técnico (tecnologias, arquitetura) |
| 5. `/speckit.tasks` | Divide o plano em tarefas pequenas |
| 6. `/speckit.analyze` | Examina cada tarefa, entende o que ela precisa e verifica se está clara antes de começar |
| 7. `/speckit.implement` | Gera o código de cada tarefa |
| 8. `/speckit.converge` | Confere se o código bate com a especificação |

---

## Inicializando SDD nos projetos

### Para projetos NOVOS (greenfield)

**Passo 1 — Crie uma pasta para o seu projeto**

Você pode fazer isso pelo Explorer do Windows, Finder do Mac ou pelo terminal:

```bash
# Escolha um local (ex: Desktop) e crie a pasta
mkdir meu-projeto
```

**Passo 2 — Abra sua IDE na pasta do projeto**

Abra sua IDE de preferência (VS Code, IntelliJ, PyCharm, etc.) e use a opção **Abrir Pasta** (ou **Open Folder**) para selecionar a pasta que você criou.

Se sua IDE tiver suporte a terminal pelo atalho `code .`, você também pode usar.

**Passo 3 — Abra o terminal na pasta do projeto**

Pela sua IDE:
- Use o **terminal integrado** da IDE (geralmente em **Terminal > Novo Terminal** ou atalho `` Ctrl + ` ``)

Ou pelo terminal do sistema:
- **Windows:** Abra o Explorer na pasta, clique em **Arquivo > Abrir Windows PowerShell** (ou digite `cmd` na barra de endereços)
- **Mac/Linux:** Clique com o botão direito na pasta e selecione **Abrir no Terminal**

O importante é que o terminal esteja **dentro da pasta do seu projeto**.

**Passo 4 — Inicialize o SpecKit**

No terminal (da IDE ou do sistema), digite:

```bash
specify init .
```

O SpecKit vai perguntar qual agente de IA você usa. Selecione **opencode** na lista.

Pronto! O SpecKit criou a estrutura `.specify/` e `specs/` dentro do seu projeto.

**Passo 5 — Abra o Opencode e comece a usar**

No mesmo terminal, digite:

```bash
opencode
```

Agora é só usar os comandos SDD. Comece com:

```text
/speckit.constitution Crie princípios de qualidade de código, testes e performance
```

Depois:

```text
/speckit.specify Crie um sistema de tarefas Kanban com quadros, colunas e cards...
```

E siga o fluxo: `/speckit.clarify` → `/speckit.plan` → `/speckit.tasks` → `/speckit.analyze` → `/speckit.implement`.

### Para projetos EXISTENTES (brownfield)

Se você já tem um projeto e quer adicionar SDD:

**Passo 1 — Abra o projeto na sua IDE**

1. IDE > **Abrir Pasta...** > selecione a pasta do seu projeto
2. Abra o terminal integrado da IDE ou o terminal do sistema na pasta do projeto

**Passo 2 — Inicialize o SpecKit no diretório atual**

```bash
specify init . --force
```

A flag `--force` permite adicionar o SpecKit em uma pasta que já tem arquivos (não apaga nada existente).

O SpecKit vai perguntar qual agente de IA usar. Selecione **opencode**.

**Passo 3 — Abra o Opencode**

```bash
opencode
```

Agora descreva a nova funcionalidade que você quer adicionar:

```text
/speckit.constitution Atualize as diretrizes considerando o código que já existe
```

```text
/speckit.specify Adicione uma tela de relatórios com gráficos de progresso...
```

```text
/speckit.plan O projeto já usa React e Node.js. Mantenha o mesmo stack.
```

E siga com `/speckit.tasks`, `/speckit.analyze` e `/speckit.implement`.

---

## Dicas para comandos mais avançados

Conforme você ganhar confiança, seja mais **específico(a)** nos comandos. Quanto mais detalhes você der, melhor será o resultado.

### Seja direta(o) na Constituição (`/speckit.constitution`)

Em vez de algo genérico como:

```text
/speckit.constitution Crie princípios de qualidade e segurança
```

Prefira algo mais completo:

```text
/speckit.constitution 
- Código deve seguir boas práticas de OOP e SOLID
- Testes unitários obrigatórios para toda regra de negócio
- Segurança: validar entrada de usuário, proteção contra SQL injection e XSS
- Performance: consultas ao banco devem usar índices, evitar N+1
- Cobertura mínima de testes: 80%
- Commits semânticos (feat:, fix:, chore:, docs:)
- Documentação obrigatória em funções públicas
```

Isso faz o agente gerar código muito mais alinhado com o que você espera.

### Seja específica(o) na Especificação (`/speckit.specify`)

| Vago | Específico |
|------|-----------|
| "Crie um sistema de tarefas" | "Crie um Kanban com colunas To Do, In Progress, In Review, Done. Cards podem ser arrastados entre colunas. Cada card tem título, descrição, responsável e data limite" |

### Seja direta(o) no Plano Técnico (`/speckit.plan`)

Diga exatamente o que usar:

```text
/speckit.plan Stack: React 18 + Vite no front, Node + Express no back, 
PostgreSQL com Prisma ORM. Autenticação JWT. Testes com Vitest. 
Deploy em Docker. Não use bibliotecas de UI prontas — CSS puro.
```

---

## Atualizando o SpecKit

```bash
# Verificar se tem versão nova
specify self check

# Atualizar
specify self upgrade
```
