# Cenário 3
## Análises do Cenário
- Quando estoque de um produto chega a zero o status é alterado automaticamente para "Pausado" ao invés de "Pausado (Sem Estoque)".
- O problema (status apresentar valor "Pausado") mantém a exibição de seu anúncio, permitindo que compras sejam realizadas.
- O cliente possui 38 itens com status "Pausado".
- O cliente não fez alteração do status.
- Atualizar manualmente o estoque implica em mudança para o status "Pausado (Sem Estoque)".
- Na imagem do log, indica que os produtos estão com estoque igual a zero.

## Evidência Visual do Problema
- O anúncio **MLB3097510082** consta como "Pausado" no painel Magazord, com estoque = 0.

## Informações da Documentação do Mercado Livre (ML)
Após leitura da documentação na parte de [Sincronização e modificação de publicações](https://developers.mercadolivre.com.br/pt_br/produto-sincronizacao-de-publicacoes) podemos entender que:
- Uma mercadoria só pode ser pausada manualmente (por decisão do usuário) ou de forma automática (quando o estoque chegar a zero).
- Além disso, há 2 tipos de status para pausa:
	- O status apresentará "Pausado (Sem Estoque)" de forma automática sempre que o estoque chegar a zero. No entanto, é possível evitar isso repondo o estoque (atribuindo available_quantity maior que zero).
	- Quando "Pausado", impede que o produto seja visualizado por outros usuário do ML. O produto não é encerrado e permite ser reativado.

## Hipóteses

| Hipótese                                                                        | Explicação                                                                                                                                                | Verificação                                                                  |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **1. O sistema está pausando o anúncio diretamente**                             | O sistema pode estar mudando o `status` para `paused`, **mas sem o motivo “sem estoque”**, visto que no log a coluna "Estoque" apresenta valor zero.              | Verificar se o sistema está usando `PUT /items/$ITEM_ID` com `status: "paused"` |
| **2. O anúncio está em modo `paused` manualmente no ML ou pelo próprio sistema** | Cliente afirma que não pausou manualmente. Pode haver trigger incorreta no banco de dados do sistema que altere o valor de `status`.                        | Verificar se algum evento automatizado pausou o anúncio erroneamente.         |
| **3. Falha de sincronização entre sistema e ML**                                    | O status `Pausado` teoricamente impede que o anúncio seja exibido normalmente, mas na prática o produto ainda aparece no marketplace, sugerindo atraso na sincronização ou falha na aplicação da regra. |  Verificar um anúncio `ativo` e outro `pausado`, e comparar o histórico de atualizações de estoque e status. |
 
 
                                 

