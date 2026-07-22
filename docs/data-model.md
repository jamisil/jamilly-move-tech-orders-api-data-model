# Modelagem de Dados

## Entidades

### Pedido (orders)

| Coluna | Tipo | Descrição |
| --- | --- | --- |
| id | TEXT (String) | Identificador único (UUID gerado automaticamente) |
| customer | TEXT (String) | Cliente associado ao pedido |
| status | TEXT (String) | Estado do pedido (padrão: open) |
| created_at | TIMESTAMP | Data e hora de criação |

### Item (items)

| Coluna | Tipo | Descrição |
| --- | --- | --- |
| id | TEXT (String) | Identificador único (UUID gerado automaticamente) |
| order_id | TEXT (String) | Chave estrangeira referenciando orders(id) |
| sku | TEXT (String) | Código identificador do produto (SKU) |
| description | TEXT (String) | Descrição detalhada do item |
| quantity | INTEGER | Quantidade comprada |

## Relacionamento

Existe um relacionamento de 1:N (um-para-muitos) entre as entidades Pedido (orders) e Item (items).

Isso significa que:
* Um Pedido pode conter vários Itens.
* Cada Item pertence a apenas um Pedido.

Comportamento do Relacionamento:
No banco de dados, essa relação é mapeada através da coluna order_id na tabela items, que atua como uma chave estrangeira referenciando a coluna id da tabela orders. O modelo está configurado com exclusão em cascata (cascade=all, delete-orphan), o que significa que, se um pedido for excluído, todos os itens atrelados a ele também serão automaticamente removidos do banco de dados.
