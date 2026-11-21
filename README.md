# 🖥️ pc-status (SoftHub Co — System & Process Executive Radar)

[![Launchpad PPA](https://img.shields.io/badge/Launchpad%20PPA-ppa%3Adiogoamb%2Ftools-orange.svg)](https://launchpad.net/~diogoamb/+archive/ubuntu/tools)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python 3](https://img.shields.io/badge/Python-3.8%2B-green.svg)](https://www.python.org/)
[![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Ubuntu%20%7C%20Debian-lightgrey.svg)]()

> **Monitor executivo de recursos, processos e containers em tempo real para terminal.**  
> Desenvolvido com foco em alta densidade de informação, baixo overhead e renderização suave com buffer alternativo de tela (estilo `htop`).

---

## ⚡ Funcionalidades

- **Métricas Globais em Tempo Real:**
  - Uso de CPU (% geral e por core) e Memória RAM / Swap.
  - Informações de Hostname, Uptime, Kernel, Arquitetura e IP de rede local.
- **Top Processos:**
  - Ordenação automática por maior consumo de CPU e RAM.
  - Identificação de PID, Usuário, Estado e Linha de comando.
- **Integração com Ecossistema DevOps:**
  - Detecção e status em tempo real de **Containers Docker** ativos.
  - Monitoramento de aplicações gerenciadas por **PM2**.
- **Mapeamento de Portas e Serviços:**
  - Visualização em 2 colunas de portas de rede em escuta (`LISTEN`), protocolos (TCP/UDP) e processos associados.
- **Interface Otimizada:**
  - Renderização via ANSI Colors e buffer de tela secundário (restaura o terminal original ao sair com `q` ou `Ctrl+C`).
  - Atualização automática sem flicker.

---

## 🚀 Instalação Oficial (Ubuntu / Debian via PPA)

O `pc-status` é distribuído oficialmente através do **Launchpad PPA** da SoftHub:

```bash
# 1. Adicionar o repositório PPA oficial
sudo add-apt-repository ppa:diogoamb/tools -y

# 2. Atualizar a lista de pacotes
sudo apt update

# 3. Instalar o pc-status
sudo apt install pc-status -y
```

Após instalado, você pode executá-lo com qualquer um dos comandos:
```bash
pc-status
# ou o alias curto:
sys-status
```

---

## 🛠️ Execução Standalone / Desenvolvimento

Não é necessário instalar compilações pesadas; o script depende apenas da biblioteca padrão do Python 3 e utilitários nativos Linux (`iproute2`, `procps`):

```bash
# Clonar o repositório
git clone https://github.com/diogoab/pc-status.git
cd pc-status

# Dar permissão de execução (se necessário)
chmod +x pc-status

# Executar
./pc-status
```

### Comandos Interativos

| Tecla | Ação |
| :--- | :--- |
| `q` | Sai da aplicação e restaura o terminal original |
| `Espaço` / `Enter` | Força uma atualização imediata das métricas |
| `Ctrl + C` | Encerramento seguro |

---

## 📦 Estrutura do Pacote Debian

O repositório já inclui os arquivos de empacotamento Debian na pasta `debian/`:
- `debian/control`: Metadados do pacote, arquitetura (`all`) e dependências.
- `debian/rules`: Regras de compilação `debhelper` e criação do symlink `/usr/bin/sys-status`.
- `debian/changelog`: Histórico de versões e release para Ubuntu Jammy (22.04 LTS) / compatíveis.

Para gerar o `.deb` localmente:
```bash
dpkg-buildpackage -us -uc -b
```

---

## 📄 Licença

Distribuído sob a licença **MIT**. Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.

Copyright (c) 2026 **Diogo Barbosa** ([SoftHub Co](https://softhubco.com.br)).
