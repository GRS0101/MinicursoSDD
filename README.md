# MinicursoSDD
Documentação do Minicurso de SDD, desde como instalar as ferramentas aos inputs para recriar os projetos apresentados

# Como instalar as Ferramentas Utilizadas
## Para instalar o Speckit do Github no terminal use o comando:

  `winget install --id Git.Git -e --source winget` para instalar git no Windows caso não tenha
  `sudo apt update && sudo apt install git -y` Para Ubuntu / Debian / Linux Mint / Pop!_OS (Baseados em Debian)
  `sudo dnf install git -y` Para Fedora
  `sudo pacman -S git --noconfirm` Para Arch Linux / Manjaro
  `sudo yum install git -y` Para Red Hat (RHEL) / CentOS
  `uv tool install specify-cli --from git+https://github.com/github/spec-kit.git@v0.12.4` para instalar o spec kit na sua máquina
    
Caso apresente erro, possivelmente é pela máquina não possuir o uv
      `powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"` para instalar o UV no windows
      `curl -LsSf https://astral.sh/uv/install.sh | sh` para instalar o UV no Linux ou MacOS

## Para instalar o opencode

  `npm i -g opencode-ai` para instalar no windows
    requer nodeJS instalado: 
  `curl -fsSL https://opencode.ai/install | bash` para instalar no Linux ou Mac
