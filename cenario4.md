# Cenário 4

## Análises, Observações e Pontos Relevantes
- Validar dados cadastrais de um sistema de gerenciamento de usuários.
- O formulário apresenta: Nome completo, E-mail, Número de telefone, Data de nascimento, Endereço (com campos para rua, cidade, estado e CEP).
- Foram realizados alterações nos campos do formulário e deve ser realizados testes que mantenham o funcionamento correto do sistema.

1. Nome Completo
| ID   | Cenário de Teste  | Entrada           | Resultado Esperado      |
| ---- | ----------------- | ----------------- | ----------------------- |
| CT01 | Nome válido       | "Fulano da Silva" | OK:   Cadastro aceito   |
| CT02 | Nome com números  | "Fulano"          | Erro: Nome inválido     |
| CT03 | Nome com símbolos | "Fulano\@Silva!"  | Erro: Nome inválido     |
| CT04 | Nome muito curto  | "F"               | Erro: Nome muito curto  |
| CT05 | Campo vazio       | ""                | Erro: Campo obrigatório |

2. E-mail
| ID   | Cenário de Teste            | Entrada                                     | Resultado Esperado      |
| ---- | --------------------------- | ------------------------------------------- | ----------------------- |
| CT06 | E-mail válido               | "teste@email.com"                           | Cadastro aceito         |
| CT07 | E-mail com formatos inválido| "teste@" ou testeteste.com                  | Erro: E-mail inválido   |
| CT08 | E-mail com espaços          | "teste @email.com"                          | Erro: E-mail inválido   |
| CT09 | Campo vazio                 | ""                                          | Erro: Campo obrigatório |

3. Número de telefone
| ID   | Cenário de Teste                | Entrada           | Resultado Esperado      |
| ---- | ------------------------------- | ----------------- | ----------------------- |
| CT10 | Telefone válido (com DDD)       | "(47) 91234-5678" | Cadastro aceito         |
| CT11 | Telefone com letras             | "(XX) 91234-5678" | Erro: Formato inválido  |
| CT13 | Telefone com menos de 9 dígitos | "12345"           | Erro: Número inválido   |
| CT14 | Campo vazio                     | ""                | Erro: Campo obrigatório |

4. Data de nascimento
| ID   | Cenário de Teste | Entrada      | Resultado Esperado      |
| ---- | ---------------- | ------------ | ----------------------- |
| CT15 | Data válida      | "01/01/2000" | Cadastro aceito         |
| CT16 | Data futura      | "01/01/2030" | Erro: Data inválida     |
| CT17 | Formato inválido | "2000-01-01" | Erro: Formato inválido  |
| CT18 | Campo vazio      | ""           | Erro: Campo obrigatório |

5. Endereço (Rua)
| ID   | Entrada              | Resultado Esperado      |
| ---- | -------------------- | ----------------------- |
| CT19 | "Av. Brasil, S/N"    | Aceito                  |
| CT20 | ""                   | Erro: Campo obrigatório |

5. Endereço (Cidade)
| ID    | Entrada     | Resultado Esperado      |
| ----- | ----------- | ----------------------- |
| CT21 | "São Paulo" | Aceito                |
| CT22 | "São 123"   | Erro: Cidade inválida |

| ID    | Entrada          | Resultado Esperado        |
| ----- | -----------      | ------------------------- |
| CT23 | "SC"             | Aceito                    |
| CT24 | "Santa Catarina" | Aceito                    |
| CT25 | "XX"             | Erro: Estado inválido     |
| CT25 | "Santa XX"       | Erro: Estado inválido     |
| CT26 | ""               | Erro: Campo obrigatório   |



5. Endereço (CEP)
| ID   | Entrada                | Resultado Esperado             |
| ---- | ---------------------  | --------------------------     |
| CT27 | "89165-063"            | Aceito                         |
| CT28 | "89165063" (sem hífen) | Aceito (considerando máscara)  |
| CT29 | "X9165063"             | Erro: Formato inválido         |
| CT30 | ""                     | Erro: Campo obrigatório        |
