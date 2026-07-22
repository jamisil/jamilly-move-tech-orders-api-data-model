# Modelagem de Dados
## Entidades
### Pedido (orders)
| Coluna | Tipo | Descrição |
|---|---|---|
| id | INTEGER | Identificador único, gerado automaticamente |
| status | TEXT | Estado do pedido (ex.: pending, completed) |
| created at | TIMESTAMP | Data e hora de criação, automática |

### Item (items)
| Coluna | Tipo | Descrição |
|---|---|---|
| id | INTEGER | Identificador único, gerado auto. |
| order id | INTEGER | Chave estrangeira orders (id) |
| title | TEXT | Nome do item |
| price | NUMERIC | Preço unitário |
| quantity | INTEGER | Quantidade |

## Relacionamento

Existe um relacionamento de 1:N (um-para-muitos) entre as entidades Pedido (orders) e Item (items). 

Isso significa que:
* Um Pedido pode conter vários Itens.
* Cada Item pertence a apenas um Pedido.

No banco de dados, essa relação é mapeada através da coluna order_id na tabela items, que atua como uma chave estrangeira referenciando a coluna id da tabela primária orders.
