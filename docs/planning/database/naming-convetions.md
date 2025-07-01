# Padrão de Nomenclatura de Objetos de Banco de Dados

## Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 28/06/2025 | 1.0    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton) |

## Descrição

Definição das diretrizes de nomenclatura a serem utilizadas em bancos de dados do projeto BRISA Helpdesk, com foco em clareza, consistência e escalabilidade.

## Regras Gerais

- Utilizar **letras minúsculas**.
- Adotar **snake_case** para separação de palavras.
- Utilizar nomes **no singular** para tabelas que representam entidades (ex: `tb_user`, `tb_product`).
- Utilizar nomes **significativos e descritivos**.
- Evitar abreviações excessivas, exceto quando bem conhecidas (ex: `dt`, `nm`, `id`, `vl`, `st`).
- Organizar objetos por **schemas prefixados com `sc_`**, representando *bounded contexts* (ex: `sc_auth`, `sc_client`).
- Adotar o inglês como língua padrão.

## Prefixos por Tipo de Objeto

| Prefixo | Tipo de Objeto           | Exemplo                            |
|---------|----------------------------|------------------------------------|
| `sc`    | Schema                     | `sc_auth`, `sc_client`             |
| `tb`    | Tabela                     | `tb_user`                       |
| `pk`    | Primary Key                | `pk_tb_user_id`                 |
| `fk`    | Foreign Key                | `fk_tb_address_tb_user_id`     |
| `uq`    | Unique Key                 | `uq_tb_user_email`              |
| `ck`    | Check Constraint           | `ck_tb_user_status`             |
| `nn`    | Not Null Constraint (não recomendado no PostgreSQL) | `nn_tb_user_email` |
| `ix`    | Índice (não único)       | `ix_tb_user_name`               |
| `ui`    | Índice Único             | `ui_tb_user_email`              |
| `sq`    | Sequence                 | `sq_tb_user_id`                 |
| `vw`    | View                     | `vw_user_ativo`                 |
| `mv`    | Materialized View        | `mv_sales_report`              |
| `fn`    | Função Escalar           | `fn_calc_user_age`         |
| `sp`    | Stored Procedure         | `sp_create_new_client`             |
| `tr`    | Trigger                  | `tr_tb_user_audit_insert`       |

## Padrão de Nomeação para Constraints e Índices

| Tipo de Constraint     | Prefixo | Formato de Nomeação                                          | Exemplo                                    |
|------------------------|---------|--------------------------------------------------------------|--------------------------------------------|
| Primary Key            | `pk_`   | `pk_{tabela}_{coluna}` ou `{coluna1}_{coluna2}`              | `pk_tb_usuario_id`                         |
| Foreign Key            | `fk_`   | `fk_{tabela_origem}_{tabela_referenciada}_{coluna}` ou `{coluna1}_{coluna2}` | `fk_tb_pedido_tb_produto_id_codigo` |
| Unique Key             | `uq_`   | `uq_{tabela}_{coluna}`                                      | `uq_tb_usuario_email`                      |
| Check Constraint       | `ck_`   | `ck_{tabela}_{coluna}`                                      | `ck_tb_usuario_status`                     |
| Not Null Constraint    | `nn_`   | `nn_{tabela}_{coluna}` (não recomendado no PostgreSQL)      | `nn_tb_usuario_email`                      |
| Índice (não único)     | `ix_`   | `ix_{tabela}_{coluna}`                                      | `ix_tb_usuario_nome`                       |
| Índice Único           | `ui_`   | `ui_{tabela}_{coluna}`                                      | `ui_tb_usuario_email`                      |
| Trigger                | `tr_`   | `tr_{tabela}_{acao}`                                        | `tr_tb_usuario_audit_insert`               |

**Observações:**
- Para colunas compostas, separe com `_` todas as colunas envolvidas.
- Para triggers, `{acao}` pode ser `insert`, `update`, `delete`, `audit`, etc.

## Convenção para Views

- Utilizar o prefixo `vw_` para views normais e `mv_` para materializadas.
- O nome deve indicar o propósito, regra de negócio ou filtro aplicado.
  
  **Exemplos:**
  - `vw_active_users`
  - `vw_monthly_sales`
  - `mv_stock_summary`

## Convenção para Funções e Procedures

- Prefixar com `fn_` (funções) e `sp_` (procedures).
- Usar verbo no infinitivo e, preferencialmente, o domínio no início do nome.

  **Exemplos:**
  - `fn_user_calculate_age`
  - `sp_client_create_new`
  - `fn_order_calculate_total`

## Convenção para Colunas de Auditoria

Para tabelas com controle de auditoria, utilizar as seguintes colunas:

| Coluna           | Significado                      |
|------------------|----------------------------------|
| `created_at`     | Data/hora de criação             |
| `created_by`     | Usuário que criou                |
| `updated_at`     | Data/hora da última atualização  |
| `updated_by`     | Usuário que atualizou            |

## Considerações Finais

- As convenções devem ser seguidas de forma consistente em **todos os schemas**.
- Para ambientes de desenvolvimento com múltiplos módulos/domínios, utilize `schemas` para **segmentação lógica**.
- Documente e versiona este padrão junto com os scripts do banco para rastreabilidade e governança.
