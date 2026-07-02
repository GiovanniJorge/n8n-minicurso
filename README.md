# n8n - Minicurso Unaerp

Projetos e exemplos usados no minicurso de n8n realizado na Unaerp — coleção organizada por tópicos e por workflows exportáveis.

## Conteúdo principal
- Workflows de exemplo para demonstrar conceitos e integrações com n8n.
- Projetos práticos focados em automação e integração de APIs.
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
Este repositório organiza exemplos práticos de automações criadas com n8n para uso didático no minicurso. Cada arquivo `.json` representa um workflow exportado do n8n que pode ser importado diretamente em sua instância local ou na nuvem.

## Estrutura do repositório
Top-level:
```text
├── LICENSE
├── README.md
└── projetos/                   # Workflows exportados (.json)
    ├── agente-com-calculadora.json
    ├── consulta-de-endereco.json
    └── verificador-de-disponibilidade-de-produtos.json
```

### Como se encaixa:
- O repositório centraliza uma coleção de fluxos de automação independentes criados para fins pedagógicos.
- Para consumir o conteúdo, basta copiar o código ou baixar os arquivos `.json` contidos na pasta `projetos/` e colá-los diretamente na área de trabalho (Canvas) de sua instância do n8n.

## Destaques do repositório

### Agente com Calculadora
* **Descrição:** Fluxo que implementa um agente inteligente capaz de realizar operações matemáticas e cálculos em resposta a solicitações do usuário.
* **Aplicações:** Demonstra o uso de Agents e integração com ferramentas de processamento de dados.

### Consulta de Endereço
* **Descrição:** Automação que realiza consultas de endereços através de APIs de geolocalização, permitindo validação e formatação de dados de CEP.
* **Aplicações:** Integração com APIs externas, tratamento de requisições HTTP e processamento de respostas JSON.

### Verificador de Disponibilidade de Produtos
* **Descrição:** Fluxo preparado para consultar e monitorar a disponibilidade de produtos em sistemas externos, com tratamento e filtragem de dados.
* **Aplicações:** Automação de e-commerce, integração com bases de dados e APIs de inventário, notificações de disponibilidade.

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

> **Importante sobre Credenciais:** Por motivos óbvios de segurança, nenhum workflow exportado armazena chaves de API, senhas ou tokens de autenticação. Após a importação, lembre-se de vincular as credenciais necessárias em cada nó que a exija.

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
