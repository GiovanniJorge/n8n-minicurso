# n8n Minicurso

<p align="center">
  <img alt="n8n" src="https://img.shields.io/badge/n8n-Automação%20e%20integração-FF6F00?logo=n8n&logoColor=white" />
  <img alt="Node.js" src="https://img.shields.io/badge/Node.js-18%2B-339933?logo=node.js&logoColor=white" />
  <img alt="JSON" src="https://img.shields.io/badge/JSON-Workflows-4B8BBE" />
  <img alt="status" src="https://img.shields.io/badge/status-ativo-brightgreen" />
  <img alt="licença" src="https://img.shields.io/badge/licen%C3%A7a-MIT-blue" />
</p>

## Sumário

- [Descrição do Projeto](#descrição-do-projeto)
- [Arquitetura e Estrutura do Repositório](#arquitetura-e-estrutura-do-repositório)
- [Como Executar Localmente](#como-executar-localmente)
- [Uso e Exemplos](#uso-e-exemplos)
- [Troubleshooting / FAQ](#troubleshooting--faq)
- [Contribuição](#contribuição)
- [Autor](#autor)
- [Licença](#licença)

## Descrição do Projeto

Este repositório reúne exemplos práticos de automações criadas com n8n, pensadas para uso didático em minicursos e treinamentos de integração. Cada arquivo dentro da pasta `projetos/` representa um workflow exportado do n8n, pronto para ser importado em uma instância local ou na nuvem.

O objetivo principal é demonstrar como criar fluxos de automação com gatilhos, chamadas HTTP, validações condicionais e respostas automatizadas. Os exemplos abordam cenários reais de uso, como consulta de endereço, verificação de disponibilidade de produtos e um agente com suporte a cálculo matemático.

A proposta do projeto é simples: permitir que o usuário visualize e importe workflows prontos, entenda a lógica por trás deles e adapte os modelos para seus próprios processos de automação.

## Arquitetura e Estrutura do Repositório

A estrutura do projeto é minimalista e focada em conteúdo pedagógico:

```text
n8n-minicurso/
├── .gitattributes
├── LICENSE
├── README.md
└── projetos/
    ├── agente-com-calculadora.json
    ├── consulta-de-endereco.json
    └── verificador-de-disponibilidade-de-produtos.json
```

### Organização dos arquivos

- `README.md`: documentação geral do repositório, instruções de uso e contexto do projeto.
- `LICENSE`: licença MIT do projeto.
- `projetos/`: pasta com os workflows exportados em formato JSON do n8n.
- `.gitattributes`: configurações de atributos de Git para padronização do repositório.

### Fluxo de dados típico

Os workflows seguem um padrão bem comum em automação com n8n:

1. Um gatilho de entrada, normalmente um `Webhook`, recebe uma solicitação.
2. O fluxo realiza uma requisição HTTP para uma API externa.
3. Uma condição verifica se a resposta atende a uma regra de negócio.
4. O workflow transforma, filtra ou formata os dados.
5. O resultado é enviado de volta ao cliente ou armazenado para uso posterior.

Exemplos do repositório:
- `consulta-de-endereco.json`: recebe dados de endereço, consulta a API do ViaCEP e responde com o resultado.
- `verificador-de-disponibilidade-de-produtos.json`: consulta produtos em uma API pública e avalia disponibilidade por estoque.
- `agente-com-calculadora.json`: combina o uso de um agente com ferramenta de cálculo para responder operações matemáticas.

## Como Executar Localmente

### Pré-requisitos

Antes de importar e executar os workflows, você precisa de:

- n8n instalado e configurado
- Node.js 18 ou superior
- Docker opcional, caso prefira rodar o n8n via container
- Acesso à internet para consultas de APIs públicas usadas nos exemplos

### Configuração de ambiente

Este repositório não contém arquivo `.env` nem segredos de ambiente. As credenciais e variáveis sensíveis são normalmente configuradas diretamente no painel do n8n, em cada nó que necessite de autenticação.

Em geral:
- Não há `.env.example` no projeto
- Não há chaves hardcoded nos arquivos exportados
- Cada workflow pode exigir credenciais após a importação

### Instalação

1. Clone o repositório:
```bash
git clone https://github.com/GiovanniJorge/n8n-minicurso.git
cd n8n-minicurso
```

2. Instale o n8n localmente usando o Node.js:
```bash
npx n8n start
```

3. Ou rode com Docker:
```bash
docker run -it --rm -p 5678:5678 n8nio/n8n
```

4. Acesse o painel do n8n em:
```text
http://localhost:5678
```

### Importando um workflow

1. Abra a interface do n8n.
2. Vá até a seção de workflows.
3. Clique em “Import from File” ou “Importar arquivo”.
4. Selecione um dos arquivos `.json` da pasta `projetos/`.
5. Ajuste as credenciais e configurações necessárias.
6. Execute o fluxo e teste a chamada.

## Uso e Exemplos

### 1) Importando o workflow de consulta de endereço

- Abra o arquivo `projetos/consulta-de-endereco.json`
- Importe no n8n
- Verifique se o webhook está ativo
- Faça uma requisição HTTP para o endpoint gerado pelo n8n
- Envie dados como:
```json
{
  "uf": "SP",
  "cidade": "São Paulo",
  "logradouro": "Avenida Paulista"
}
```

### 2) Verificando disponibilidade de produtos

- Importe `projetos/verificador-de-disponibilidade-de-produtos.json`
- Configure o webhook
- Envie um termo de busca como:
```json
{
  "termo": "smartphone"
}
```

O fluxo consulta uma API externa e retorna os itens com estoque disponível e indisponível.

### 3) Agente com calculadora

- Importe `projetos/agente-com-calculadora.json`
- Conecte uma chave da API do Groq no nó de modelo
- Execute o workflow no editor do n8n
- Faça perguntas como:
```text
Qual é o valor final de 250 com 15% de desconto?
```

O agente pode usar a ferramenta de cálculo para responder com precisão.

## Troubleshooting / FAQ

### O workflow não importa
- Verifique se sua instância do n8n está atualizada.
- Confirme que o arquivo `.json` não foi corrompido.
- Tente importar em uma versão compatível do n8n.

### O webhook não responde
- Verifique se o workflow está ativo.
- Confirme se o endpoint foi configurado corretamente.
- Certifique-se de que o n8n está em execução e acessível no servidor.

### Erro em credenciais
- Acesse o painel do n8n e configure as credenciais dos nós.
- Verifique se as APIs exigem token, chave ou autenticação específica.
- O projeto não inclui segredos e não deve armazenar credenciais no repositório.

### Consulta de API falha
- Verifique se a API externa está disponível.
- Valide se o endpoint, método HTTP e parâmetros estão corretos.
- Teste as requisições manualmente com curl ou Postman.

### O projeto parece não ter código-fonte
- Isso é esperado: o repositório é uma coleção de workflows exportados do n8n, e não uma aplicação tradicional em Node.js ou Python.

## Contribuição

Contribuições são bem-vindas. Se você quiser colaborar com novos fluxos, melhorar a documentação ou ajustar exemplos existentes:

1. Faça um fork do repositório.
2. Crie uma branch para sua alteração.
3. Faça commits com mensagens claras e objetivas.
4. Abra um pull request descrevendo o que foi melhorado.
5. Mantenha o foco em qualidade didática e clareza dos exemplos.

## Autor

- Nome: Giovanni Jorge
- GitHub: [@GiovanniJorge](https://github.com/GiovanniJorge)

## Licença

Este projeto está licenciado sob a licença MIT.

Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.

