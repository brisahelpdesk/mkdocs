# AuditModule (Módulo de Auditoria)

O `AuditModule` é responsável por registrar e monitorar ações críticas realizadas no sistema, garantindo rastreabilidade, segurança e conformidade. Ele é essencial para acompanhar eventos como alterações em chamados, acessos administrativos, mudanças em contratos, entre outros.

---

## Objetivo Principal

Rastrear quem fez o quê, quando e em qual contexto dentro da aplicação.

---

## O que o AuditModule registra

| Tipo de Ação                        | Exemplo                                                    |
|------------------------------------|-------------------------------------------------------------|
| Login e logout                     | Entrada de um usuário no sistema                            |
| Alteração de dados críticos        | Edição de chamados, contratos, perfis                       |
| Exclusão de registros              | Remoção de artigos ou produtos                              |
| Acesso a relatórios sensíveis      | Download de relatórios gerenciais                           |
| Falhas de autenticação             | Tentativas de login mal-sucedidas                           |
| Alterações de permissões           | Usuário promovido a supervisor                              |
| Ações administrativas              | Execução de backup ou scripts                               |
