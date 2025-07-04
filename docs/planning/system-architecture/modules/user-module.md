# UserModule (Módulo de Gerenciamento de Usuários)

O `UserModule` é responsável por gerenciar os dados dos usuários do sistema, incluindo seu cadastro, atualização de informações, definição de perfis de acesso e ativação/desativação de contas. Ele também interage com o módulo de autenticação para garantir segurança e controle de permissões.

---

## Objetivo Principal

Permitir o controle completo do ciclo de vida dos usuários da plataforma, garantindo que apenas pessoas autorizadas tenham acesso e possam exercer suas funções com os privilégios apropriados.

---

## O que o UserModule faz

| Função                           | Descrição                                                                |
| -------------------------------- | ------------------------------------------------------------------------ |
| Cadastro de usuários             | Permite ao administrador criar novos usuários com perfis e permissões    |
| Edição de informações pessoais   | Atualização de nome, e-mail, telefone, entre outros dados                |
| Atribuição de perfis             | Define o tipo de usuário (Administrador, Supervisor, Atendente, Cliente) |
| Ativação e desativação de contas | Controla o status da conta sem necessidade de exclusão permanente        |
| Integração com autenticação      | Interage com o módulo de autenticação para validar e aplicar permissões  |
