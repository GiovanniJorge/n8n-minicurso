# n8n - Minicurso Unaerp

Projetos e exemplos usados no minicurso de n8n realizado na Unaerp — coleção organizada por tópicos e por workflows exportáveis.

## Conteúdo principal
- Workflows de exemplo para demonstrar conceitos e integrações com n8n.
- Pastas organizadas por tema (APIs, automação de planilhas, integração com e-mail, etc.).
- Cada workflow está disponível no formato exportável do n8n (.json) e acompanhado de documentação de execução quando aplicável.

## Badges
![Licença](https://img.shields.io/github/license/GiovanniJorge/n8n-minicurso?style=flat-square)

## Sumário
- [Visão geral](#visão-geral)
- [Estrutura do repositório](#estrutura-do-repositório)
- [Destaques do repositório](#destaques-do-repositório)
- [Como executar e importar workflows](#como-executar-e-importar-workflows)
- [Contribuindo](#contribuindo)
- [Licença](#licença)
- [Autor / Contato](#autor--contato)

## Visão geral
Este repositório organiza exemplos práticos de automações criadas com n8n para uso didático no minicurso. Cada arquivo `.json` representa um workflow exportado do n8n que pode ser importado diretamente em sua instância local ou na nuvem. Os exemplos variam desde tarefas simples (gatilhos e transformações de dados) até cenários complexos com webhooks e integrações de APIs.

## Estrutura do repositório
Top-level:
```text
├── LICENSE
├── README.md
├── workflows/                 # Workflows exportados (.json) agrupados por tema
│   ├── apis/                  # Integração com APIs externas e Webhooks
│   │   ├── github-webhook.json
│   │   └── weather-api.json
│   ├── google-sheets/         # Automação de leitura e escrita em planilhas
│   ├── email/                 # Disparos de e-mail e processamento de inbox
│   └── utils/                 # Workflows utilitários (Parsers de CSV, validações)
├── docs/                      # Documentação adicional e guias conceituais
├── scripts/                   # Scripts auxiliares para importação em lote
└── assets/                    # Arquivos fictícios de teste (CSVs, layouts, etc.)
```

### Como se encaixa:
- O repositório centraliza uma coleção de fluxos de automação independentes criados para fins pedagógicos.
- Para consumir o conteúdo, basta copiar o código ou baixar os arquivos `.json` contidos na pasta `workflows/` e colá-los diretamente na área de trabalho (Canvas) de sua instância do n8n.

## Destaques do repositório

### GitHub Webhook Integration
* **Descrição:** Fluxo preparado para recepção de eventos e gatilhos automatizados disparados a partir de webhooks estruturados do GitHub.
* **Nodes Principais:** Webhook Node, Set Node, IF Node.

### Weather API Sync
* **Descrição:** Consumo periódico de dados climáticos via requisição HTTP externa com tratamento e filtragem de propriedades JSON.
* **Nodes Principais:** Cron/Schedule Node, HTTP Request Node, Code Node (JavaScript).

## Como executar e importar workflows

### Pré-requisitos
- Instância ativa do n8n (Local, Docker ou Cloud)
- Node.js (v18 ou superior se for executar localmente via npm)

### Inicialização rápida do n8n (Ambiente Local)

* **Via NPX (Sem instalação global):**
```bash
npx n8n start
```

* **Via Docker Core:**
```bash
docker run -it --rm -p 5678:5678 n8nio/n8n
```
Após iniciar, acesse o painel de controle em `http://localhost:5678`.

### Importando um fluxo

1. Abra o painel da sua instância local do n8n.
2. Crie um novo workflow em **Workflows -> Add Workflow**.
3. No menu de opções (três pontos no canto superior direito), selecione **Import from File** e escolha o arquivo `.json` desejado deste repositório.
4. *Alternativa:* Abra o arquivo `.json` em seu editor de texto, copie o código completo (Ctrl+C) e cole (Ctrl+V) diretamente no Canvas do n8n.

> **Importante sobre Credenciais:** Por motivos óbvios de segurança, nenhum workflow exportado armazena chaves de API, senhas ou tokens de autenticação. Após a importação, lembre-se de vincular suas próprias credenciais mockadas ou de teste dentro das configurações de cada Node específico.

## Contribuindo
Contribuições são bem-vistas! Se deseja sugerir um novo fluxo de automação utilitário ou corrigir rotinas em JavaScript dentro do Code Node, siga os passos abaixo:

1. Faça um **Fork** do repositório.
2. Crie uma branch com nome descritivo: `feature/workflow-nome` ou `fix/readme`.
3. Faça commits atômicos com mensagens claras e objetivas.
4. Abra um **Pull Request** detalhando as alterações implementadas e a proposta educacional do fluxo.

## Licença
Este repositório utiliza a licença MIT — consulte o arquivo [LICENSE](LICENSE) na raiz.

## Autor / Contato
- **Autor:** Giovanni Jorge  
- **Repositório:** [https://github.com/GiovanniJorge/n8n-minicurso](https://github.com/GiovanniJorge/n8n-minicurso)
