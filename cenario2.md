# 2º Cenário

## Análises, Observações e Pontos Relevantes
- Será analisado um projeto de integração com [Bling](https://developer.bling.com.br/bling-api), para gerenciar estoque, em um e-commerce.
- Os desenvolvedores finalizaram a implementação da integração.
- Deve ser realizados testes da integração, com foco na funcionalidade.
- Similar ao cenário 1, neste caso haverá algumas repetições de ideias do cenário anterior.

## 1. Documentação e Materiais de Apoio
### 1.1 Identificação da documentação
- Vamos precisar da documentação de requisitos gerais.
- Documentações do sistema de versões anteriores do e-commerce.
- Obrigatório a documentação oficial da API do sistema Bling.
- Diagrama de fluxo de dados entre o e-commerce e o sistema Bling.

### 1.2 Mapeamento dos requisitos
- Precisaremos utilizar uma matriz de rastreabilidade para associar requisitos com os cenários de testes.
- Será necessário avaliar as entradas de dados (itens movimentados pelo e-commerce para o gerenciador de estoque Bling).
- E também avaliar as saídas dos dados (dados processados retornados pelo bling para o e-commerce).

### 1.3 Utilização de ferramentas
- Jira, para gerenciamento dos requisitos.
- Lucidchart, para modelagem de fluxos.
- Postman/SwaggerUI, para avaliar respostas da API de integração.

## 2. Abrangência dos Testes
### 2.1 Funcionalidades
- Devem ser testadas as sincronizações de produtos, como SKU, categorias, preços, descrições).
- Atualizações de estoque manualmente (identificação SKU, alterações de valores, quantidades, valores).
- Atualizações de estoque motivados por compras e vendas.
- Tratamento de logs.
- Sincronia com NF, contas à pagar e receber.

### 2.2 Priorização dos testes
- Alta: Funções com impacto direto no faturamento (pedidos, estoque, emissão de NF, boletos).
- Média: Operações CRUD e sincronização de NF.
- Baixa: Logs.

Critérios gerais de priorização:
- Criticidade para o negócio.
- Dependência com outras integrações.
- Complexidade técnica e histórico de falhas.

## 3. Execução dos Testes
### 3.1 Dados de teste
- Os dados podem ser fictícios inserindo-os manualmente ou por meio de um arquivo de mocking.
- Estabelecer, em todos os módulos, diversas variações conforme necessidade como preço, descontos, quantidades, tamanho, tipos de entrega, etc.
- Informações validas e inválidas para as funcionalidade principais do estoque.
- Geração de pedidos e devoluções que influenciam diretamente no estoque.

### 3.2 Ferramentas de automação
- Postman para inpeções rápidas das saída de dados provenientes da API.
- Cypress, para a manipulação do estoque.
- CI/CD com Jenkins ou GitHub Actions para integração dos testes automatizados.

### 3.3 Registro de resultados
- Os resultados serão anotados em diferentes documentos.
	- Documentação dos testes que comprovam eficiência e eficácia do sistema através dos testes, bem com servirá para comprovação/veracidade dos testes.
	- Documentação interna para disponibilizar entre os membros da equipe e de demais setores para que todos tomem conhecimento das mudanças e novidades.
	- Documentação para o cliente, por meio de Notas de Atualização, para que o cliente fique em sintonia com o desenvolvimento.
- Uma planilha com postos-chaves, sem muito detalhes, que faça um "link" com os documentos gerados que podem servir para reuniões na spring retrospective e auditorias.
