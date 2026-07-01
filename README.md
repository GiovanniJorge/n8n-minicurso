# n8n - Minicurso Unaerp
Projetos e exemplos usados no minicurso de n8n realizado na Unaerp — colecção organizada por tópicos e por workflows exportáveis.

## Conteúdo principal
- Workflows de exemplo para demonstrar conceitos e integrações com n8n.
- Pastas organizadas por tema (APIs, automação de planilhas, integração com e-mail, etc.).
- Cada workflow está disponível no formato exportável do n8n (.json) e acompanhado de README/README de execução quando aplicável.

## Badges
- Licença: MIT (ver arquivo LICENSE)

## Sumário
- [Visão geral](#visão-geral)
- [Estrutura do repositório](#estrutura-do-reposit%C3%B3rio)
- [Como executar e importar workflows](#como-executar-e-importar-workflows)
- [Boas práticas / recomendações](#boas-pr%C3%A1ticas--recomenda%C3%A7%C3%B5es)
- [Contribuindo](#contribuindo)
- [Testes e automação (opcional)](#testes-e-automa%C3%A7%C3%A3o-opcional)
- [Licença](#licen%C3%A7a)
- [Autor / Contato](#autor--contato)

## Visão geral
Este repositório organiza exemplos práticos de automações criadas com n8n para uso didático no minicurso. Cada arquivo `.json` representa um workflow exportado do n8n que pode ser importado em sua instância local ou na nuvem do n8n. Os exemplos variam desde tarefas simples (gatilhos e transformações) até integrações com APIs externas e manipulação de dados.

Objetivo:
- Fornecer material prático e reprodutível para alunos.
- Servir como base para exercícios e adaptações em sala.
- Demonstrar padrões e boas práticas de construção de workflows no n8n.

## Estrutura do repositório
Top-level:
- LICENSE
- README.md
- workflows/                  — workflows exportados (.json) agrupados por tema
  - apis/                     — exemplos de integração com APIs externas
    - github-webhook.json
    - weather-api.json
  - google-sheets/            — exemplos de leitura/escrita em planilhas
  - email/                    — exemplos de envio e processamento de e-mail
  - utils/                    — workflows utilitários (ex.: parse CSV, validações)
- docs/                       — documentação adicional e instruções por pasta (opcional)
- scripts/                    — scripts úteis (ex.: import em lote, validação)
- assets/                     — arquivos de exemplo usados pelos workflows (CSV, imagens, etc.)

Como se encaixa:
- Cada arquivo `.json` é um workflow exportado do n8n. Para usar, importe-o na sua instância do n8n.
- Pastas e nomes devem ser auto-explicativos. Acrescente um pequeno README em cada subpasta quando um conjunto de workflows exigir contexto.

## Como executar e importar workflows
Pré-requisitos (exemplos):
- Ter uma instância do n8n rodando localmente, em servidor ou usar o n8n.cloud.
- Recomenda-se Node.js 18+ para instalações locais (ver docs oficiais do n8n).

Executando n8n localmente (exemplos rápidos):
- Via npx:
  - npx n8n start
- Via Docker (modo rápido):
  - docker run -it --rm -p 5678:5678 n8nio/n8n

Importando um workflow via interface (GUI):
1. Abra sua instância do n8n (ex.: http://localhost:5678).
2. Vá em Workflows → Import.
3. Selecione o arquivo .json (ou cole o JSON) e importe.

Importando via CLI/API (exemplo):
- É possível importar/exportar workflows via CLI ou API do n8n (consulte a documentação oficial do n8n para comandos e endpoints atuais).
- Caso deseje automatizar a importação em lote, coloque scripts em `scripts/` que usem as ferramentas/endpoint do n8n.

Executando um workflow:
- Após importar, ative os nodes que necessitam de credenciais e configure as credenciais no n8n.
- Salve e execute manualmente ou habilite gatilhos conforme o caso.

Observação sobre credenciais e dados sensíveis:
- Não inclua credenciais ou tokens nos arquivos do repositório.
- Use as credenciais do n8n (credential manager) ou variáveis de ambiente na sua instância.

## Boas práticas / recomendações
- Use nomes descritivos para workflows e nodes.
- Documente o objetivo do workflow no campo Description do n8n e, quando necessário, em um README na pasta correspondente.
- Não versionar segredos: nunca comite credenciais ou arquivos .env com chaves.
- Para dados de exemplo (CSV, JSON), armazene em `assets/` e marque claramente que são dados fictícios.
- Sempre validar o JSON exportado antes de compartilhar (por exemplo: jsonlint, ou importação teste numa instância isolada).
- Versão dos recursos: anote na documentação a versão do n8n recomendada para reproduzir os exemplos.

## Contribuindo
Contribuições são bem-vindas (ex.: novos workflows, correções, exemplos, documentação). Fluxo sugerido:
1. Fork do repositório.
2. Criar branch com nome descritivo: `feature/workflow-nome` ou `fix/readme`.
3. Fazer commits atômicos com mensagens claras.
4. Abrir Pull Request descrevendo as mudanças e o objetivo pedagógico.
5. Se possível, inclua um pequeno README por workflow explicando:
   - Descrição do fluxo;
   - Entradas/saídas esperadas;
   - Como testar localmente.
6. Para workflows que dependem de serviços externos, documente steps para criar credenciais de teste (sempre com dados fictícios).

Sugestões adicionais:
- Adicionar um README por pasta explicando o objetivo e pré-requisitos.
- Incluir scripts em `scripts/` para validar ou importar workflows em lote.
- Considerar adicionar exemplos de variáveis/credenciais mockadas para testes locais.

## Testes e automação (opcional)
- É possível criar um workflow de CI que:
  - Valide sintaticamente os arquivos JSON (jsonlint).
  - Tente importar os workflows em uma instância n8n de teste para detectar erros de schema (via API/CLI).
- Um GitHub Actions simples poderia:
  - Executar jsonlint em `workflows/**/*.json`.
  - Rodar testes unitários/integração dos scripts em `scripts/`.

## Licença
Este repositório utiliza a licença MIT — consulte o arquivo `LICENSE` na raiz.

## Autor / Contato
Autor: Giovanni Jorge  
Repositório: https://github.com/GiovanniJorge/n8n-minicurso
