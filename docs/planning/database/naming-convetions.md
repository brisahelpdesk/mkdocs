# Padrão de Nomenclatura de Banco de Dados

## 1. Regras Gerais

- Utilizar **letras minúsculas**.
- Adotar **snake_case** para separação de palavras.
- Use nomes no singular para tabelas que representam **entidades** (`tb_usuario`, `tb_produto`).
- Para views, indique o propósito ou filtro aplicado (`vw_usuario_ativo`, `vw_vendas_mensais`).

---

## 2. Prefixos por Tipo de Objeto

| Prefixo | Tipo de Objeto           | Exemplo                            |
|---------|--------------------------|------------------------------------|
| `sc`    | Schema                   | `sc_financeiro`                    |
| `tb`    | Tabela                   | `tb_usuario`                       |
| `pk`    | Primary Key              | `pk_tb_usuario_id`                 |
| `fk`    | Foreign Key              | `fk_tb_endereco_tb_usuario_id`     |
| `uk`    | Unique Key               | `uk_tb_usuario_email`              |
| `ck`    | Check Constraint         | `ck_tb_usuario_status`             |
| `ix`    | Índice                   | `ix_tb_usuario_nome`               |
| `ui`    | Índice Único             | `ui_tb_usuario_email`              |
| `sq`    | Sequence                 | `sq_tb_usuario_id`                 |
| `vw`    | View                     | `vw_usuario_ativo`                 |
| `mv`    | Materialized View        | `mv_relatorio_vendas`              |
| `fn`    | Função Escalar           | `fn_calcula_desconto`              |
| `sp`    | Stored Procedure         | `sp_cria_usuario`                  |
| `tr`    | Trigger                  | `tr_tb_usuario_audit`              |

---

## 3. Padrão de Nomeação para Constraints

### Tabela de Padrões para Constraints

| Tipo de Constraint     | Prefixo | Formato de Nomeação                                     | Exemplo                                  |
|------------------------|---------|----------------------------------------------------------|-----------------------------------------|
| **Primary Key**        | `pk_`   | `pk_{tabela}_{coluna}`                                  | `pk_tb_usuario_id`                       |
| **Foreign Key**        | `fk_`   | `fk_{tabela_origem}_{tabela_referenciada}_{coluna}`     | `fk_tb_endereco_tb_usuario_usuario_id`   |
| **Unique Key**         | `uk_`   | `uk_{tabela}_{coluna}`                                  | `uk_tb_usuario_email`                    |
| **Check Constraint**   | `ck_`   | `ck_{tabela}_{coluna}`                                  | `ck_tb_usuario_status`                   |
| **Not Null Constraint** | `nn_`   | `nn_{tabela}_{coluna}`                                    | `nn_tb_usuario_email`             |
| **Índice (não único)** | `ix_`   | `ix_{tabela}_{coluna}`                                  | `ix_tb_usuario_nome`                     |
| **Índice Único**       | `ui_`   | `ui_{tabela}_{coluna}`                                  | `ui_tb_usuario_email`                    |
| **Trigger**            | `tr_`   | `tr_{tabela}_{acao}`                                    | `tr_tb_usuario_audit_insert`             |

#### Observações
- Para colunas compostas, separe os nomes com underscore. Por exemplo: `pk_tb_pedido_id_numero`.
- Para triggers, o sufixo `{acao}` pode indicar a operação: `insert`, `update`, `delete`, etc.
- Para views, indique o propósito ou filtro aplicado (`vw_usuario_ativo`, `vw_vendas_mensais`).
