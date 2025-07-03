# 1º Cenário

## Análises, Observações e Pontos Relevantes
- O time de desenvolvedores concluiu o projeto de integração de marketplaces de terceiros em um e-commerce. ([Mercado Livre](https://developers.mercadolivre.com.br/pt_br/api-docs-pt-br), [Amazon](https://developer.amazonservices.com/pt-br))
- O projeto envolve integração de estoque, anúncios, faturamento, pedidos e preço.
- Diante deste contexto, deve ser realizados testes no projeto concluído, com foco na funcionalidade.


## 1. Documentação e Materiais de Apoio
### 1.1 Identificação da documentação
- Documentos de requisitos gerais.
- Documentações do sistema de versões anteriores do e-commerce
- Obrigatório a documentação oficial da API dos marketplaces.
- Diagrama de fluxo de dados entre o e-commerce e marketplaces.

### 1.2 Análise da documentação
- Leitura crítica e atenta aos detalhes das documentações das APIs
	- Endpoints (headers, status, métodos, http).
	- Estruturas de respostas.
- Identificar as regras de negócios específicas de cada marketplace, como politica de fretes, identificar campos de preenchimento obrigatório, e identificações de produtos (SKU).

### 1.3 Mapeamento dos Requisitos
- Matriz de rastreabilidade dos requisitos para relacionar requisitos com os casos de testes.
- Criar casos de testes com base em histórias de usuários envolvendo critérios de aceitação.

### 1.4 Ferramentas utilizadas
- Jira, para gerenciamento dos requisitos e histórias de usuários.
- Lucidchart, para mapeamento de fluxos
- Postman/SwaggerUI, para verificação de respostas dos endpoints.
- Cypress para criação de testes unitários e interatividade do sistema.

## 2. Abrangência dos Testes
### 2.1 Funcionalidades
- Sincronização com estoques (operações CRUD)
- Validações em preços (operações CRUD)
- Validações de anúncios (UI/UX)
- Validação de recebimento e atualizações de dados (pessoais e pedidos)
- Validações de segurança (tokens de autenticação, exposição de dados sensíveis)

### 2.2 Casos de uso
| Funcionalidade | Casos de Sucesso             | Casos de Falha               | Teste de Carga                                        | Testes de API        |
| -------------- | ---------------------------- | ---------------------------- | ----------------------------------------------------- | -------------------- |
| Estoque        | SKU atualizado corretamente  | SKU inexistente (404)        | Atualização de 10.000 SKUs simultaneamente            | POST /cadastrar      |
| Anúncios       | Produto criado com sucesso   | Dados obrigatórios ausentes  | Cadastro em massa                                     | PUT /item/{id}       |
| Pedidos        | Pedido recebido e processado | Status inválido (família 400)| Picos dfe acesso simulados em datas promocionais      | GET /pedidos         |
| Faturamento    | Nota fiscal emitida          | Falha na validação impostos  | Envio de lote de 10.000 NFs                           | POST /notas          |
| Preço          | Atualização aplicada         | Preço negativo (422)         | Atualização simultânea de 10.000 produtos             | PATCH /preco         |
| Segurança      | Token válido e expiração     | Acesso sem autenticação      | Teste com múltiplos usuários simultâneos              | Validação de headers |

### 2.3 Priorização dos testes
- Alta prioridade: Financeiro (contas à pagar/à receber, emissão de NF, boletos, valores em geral), segurança e desempenho.
- Média prioridade: Controle de estoque (quantidade e valores monetários)
- Baixa prioridade: UI/UX, layout, estilização em geral, aplicação de máscaras em campos de preenchimento.

Critérios de priorização:
- Impacto no faturamento
- Visibilidade para o cliente final
- Interoperabilidade com outros sistemas e módulos.
- Histórico de incidentes passados

## Execução dos Testes
### 3.1 Ambiente de Teste
- Todos os testes de funcionalidade devem ser feitos em ambiente de homologação.
- Testes de desempenho podem ser feitos em ambiente de produção.

### 3.2 Dados de teste
- Os dados podem ser fictícios inserindo-os manualmente ou por meio de um arquivo de mocking.
- Estabelecer, em todos os módulos, diversas variações conforme necessidade como preço, descontos, quantidades, tamanho, tipos de entrega, etc.
- Informações validas e inválidas para itens, pedidos, NF, financeiro.

### 3.3 Ferramentas de automação
- Postman: Para testes das APIs
- Cypress: Para testes automatizados e teste de sistema
- Docker: Isolamento para testes de integração em diferentes ambientes (desktop/mobile e sistemas operacionais Android, Windows, iOS...) 
- CI/CD com Jenkins ou GitHub Actions para integração dos testes automatizados

### 3.4 Registro de resultados
- Deve-se registrar todas as novas funcionalidades e outras que sofreram alterações em documentos com textos e imagens autoexplicativas.
- Redigir um documento comprovando a veracidade, eficiência e eficácia dos testes.
- Deve ser feito um documento interno para que todos os membros possam tomar conhecimento da atualização do produto.
- Um outro documento a ser disponibilizado para os clientes para que possam entender o comportamento e funcionamento do projeto realizado.
- Uma planilha com postos-chaves, sem muito detalhes, que faça um "link" com os documentos gerados que podem servir para reuniões na spring retrospective e auditorias.
