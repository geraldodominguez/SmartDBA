# 🧠 SmartDBA Toolkit

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg?style=flat-square)
![Maintenance](https://img.shields.io/badge/maintained-yes-green.svg?style=flat-square)
![Platform](https://img.shields.io/badge/platform-SQLServer%20%7C%20Oracle%20%7C%20PostgreSQL-lightgrey?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-yellow.svg?style=flat-square

> **Automação inteligente, segura e padronizada para o DBA moderno.**

O **SmartDBA** é uma suíte de ferramentas (Stored Procedures e Scripts) projetada para centralizar e profissionalizar a administração de bancos de dados. Ele elimina a necessidade de scripts soltos e sem versão, oferecendo um kit auditável para manutenção, performance e segurança

---

## 📋 Índice

* [Funcionalidades](#-funcionalidades)
* [Estrutura](#-estrutura-do-projeto)
* [Instalação](#-instalação-e-configuração)
* [Como Usar](#-como-usar-exemplos)
* [Roadmap](#-roadmap)
* [Disclaimer](#-isenção-de-responsabilidade-disclaimer)
* [Contribuição](#-como-contribuir)
* [Licença](#-licença)

---




## 🚀 Funcionalidades Principais

O projeto foca em resolver os pilares da administração de dados: **Manutenção, Performance, Integridade e Segurança**.

### 🛠️ SQL Server (T-SQL)
Atualmente o módulo mais completo, contendo procedimentos armazenados no banco `DBA`:

* **Gestão de Espaço:** `spu_ShrinkAllDataFiles` - Shrink inteligente com análise de impacto e simulação ("What-if").
* **Manutenção de Índices:** `spu_RebuildAllIndexes` - Rebuild baseado em análise real de fragmentação.
* **Estatísticas:** `spu_UpdateAllStatistics` - Atualização baseada no contador de modificações (`modification_counter`).
* **Integridade:** `spu_CheckDatabaseIntegrity` - Wrapper otimizado para `DBCC CHECKDB` com suporte a *Physical Only*.
* **Tuning:** `spu_Diagnostico_IndicesFaltantes` - Análise de DMVs para sugerir criação automática de índices de alto impacto.

### 🔮 Oracle (PL/SQL)
* *Em desenvolvimento: Scripts de Tablespace e Monitoramento de Sessão.*

### 🐘 PostgreSQL (PL/pgSQL)
* *Em desenvolvimento: Vacuum Analysis e Bloat check.*

---

## 📂 Estrutura do Repositório

O projeto segue uma hierarquia baseada em Tecnologia > Categoria:

```text
SmartDBA/
├── SQLServer/
│   ├── 00-Setup/          # Scripts de criação do ambiente (Database DBA)
│   ├── 01-Maintenance/    # Rotinas de disco e integridade
│   ├── 02-Performance/    # Tuning, Índices e Estatísticas
│   └── 03-Monitoring/     # Views de monitoramento
├── Oracle/
│   └── ...
├── PostgreSQL/
│   └── ...
└── Templates/             # Modelos de cabeçalho e padronização de código

---

## 📦 Instalação e Configuração

### Pré-requisitos
Antes de começar, certifique-se de ter em seu ambiente:
* **Git** instalado e configurado.
* **Cliente SQL** de sua preferência (SSMS, Azure Data Studio, DBeaver ou SQLPlus).

### Passo a Passo (SQL Server)

**1. Clone o repositório**
Abra seu terminal e baixe os arquivos para sua máquina local:

```bash
git clone [https://github.com/SEU-USUARIO/SmartDBA.git](https://github.com/geraldodominguez/SmartDBA.git)
cd SmartDBA

---
2. Crie o Banco de Dados de Administração O kit foi desenhado para rodar em um banco centralizado chamado DBA. Execute o script SQLServer/00-Setup/create_database_dba.sql ou rode o comando abaixo na sua instância:

SQL

USE master;
GO

IF NOT EXISTS (SELECT * FROM sys.databases WHERE name = 'DBA')
BEGIN
    CREATE DATABASE [DBA];
    PRINT 'Database [DBA] criado com sucesso.';
END
GO
3. Implantar as Ferramentas Conecte-se ao banco DBA recém-criado e execute os scripts .sql na seguinte ordem:

Scripts da pasta 01-Maintenance (Ex: Shrink, Integridade).

Scripts da pasta 02-Performance (Ex: Índices, Estatísticas).

🎮 Como Usar (Exemplos)
Todas as procedures possuem um modo de Simulação (@Executar = 0) ativado por padrão. Isso garante segurança antes de rodar em produção.

Exemplo: Diagnóstico de Saúde dos Índices Verifica fragmentação e sugere Rebuild ou Reorganize.

SQL

EXEC [DBA].[dbo].[spu_RebuildAllIndexes] @Executar = 0;
Exemplo: Verificar Integridade (Rápido) Executa DBCC CHECKDB apenas na estrutura física.

SQL

EXEC [DBA].[dbo].[spu_CheckDatabaseIntegrity] 
    @PhysicalOnly = 1, 
    @Executar = 1;

--- 

## ⚖️ Isenção de Responsabilidade (Disclaimer)

LEIA COM ATENÇÃO ANTES DE USAR:

Este software é fornecido "como está", sem garantia de qualquer tipo, expressa ou implícita. O uso destas ferramentas e scripts é de inteira responsabilidade do usuário.
Teste Sempre: Jamais execute scripts de manutenção em Produção sem antes validar em um ambiente de Desenvolvimento/Homologação (Staging).
Impacto: Operações como REBUILD INDEX, UPDATE STATISTICS ou DBCC CHECKDB podem causar bloqueios (locks) e alto consumo de recursos. Execute apenas em janelas de manutenção apropriadas.
Backups: Certifique-se de ter backups validados antes de realizar alterações estruturais.
O autor e os contribuidores deste repositório não se responsabilizam por quaisquer danos, perda de dados, interrupção de serviço ou prejuízos financeiros decorrentes do uso (correto ou incorreto) destes scripts.

---

🤝 Como Contribuir
Contribuições são bem-vindas! Se você tem um script útil ou encontrou um bug:

Faça um Fork do projeto.
Crie uma Branch para sua Feature (git checkout -b feature/minha-nova-proc).
Faça o Commit e o Push.
Abra um Pull Request.

---

👤 Autor

Geraldo Dominguez

💼 LinkedIn: Geraldo Dominguez
🐙 GitHub: @SeuUsuario

📧 Contato: seu.email@exemplo.com


---
<div align="center"> <sub>Feito com ❤️ para a comunidade DBA.</sub> </div>

## 📄 Licença

Este projeto está sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

❤️ Apoie o projeto
Se este toolkit te ajudou a otimizar seu banco de dados, considere dar uma ⭐️ no repositório!
## 👤 Autor

**Geraldo Dominguez**

* 💼 **LinkedIn:** [Seu Perfil no LinkedIn](https://www.linkedin.com/in/geraldodominguez)
* 🐙 **GitHub:** [@SeuUsuario](https://github.com/geraldodominguez)

---

## ❤️ Apoie o projeto

Se este projeto te ajudou a economizar tempo ou salvou seu banco de dados, dê uma ⭐️ no repositório!