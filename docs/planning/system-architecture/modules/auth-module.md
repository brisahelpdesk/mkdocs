# AuthModule (Módulo de Autenticação)

O `AuthModule` é responsável por gerenciar o acesso seguro ao sistema, incluindo autenticação com e-mail e senha, verificação em dois fatores (2FA), gerenciamento de perfis e controle de sessão. Também lida com o primeiro acesso, troca obrigatória de senha e validação por pergunta de segurança.

---

## Objetivo Principal

Garantir que apenas usuários autenticados e autorizados acessem o sistema, com segurança reforçada, validação por múltiplos fatores e controle de permissões por perfil.

---

## O que o AuthModule faz

| Função                                | Descrição                                                                 |
|--------------------------------------|---------------------------------------------------------------------------|
| Login com e-mail e senha             | Autenticação principal com verificação de credenciais                     |
| Autenticação em dois fatores (2FA)   | Verificação de código enviado por e-mail após o login                     |
| Primeiro acesso seguro               | Força troca de senha e configuração de pergunta de segurança              |
| Perfis de acesso                     | Controle de permissões por tipo de usuário (CLI, ATD, SUP, ADM)           |
| Sessão e renovação de token          | Uso de JWT para sessão e refresh token quando necessário                  |
| Recuperação de senha                 | Redefinição com verificação via pergunta de segurança                     |

---

## Relacionamento com Serviços Externos

| Serviço              | Papel                                                                 |
|----------------------|-----------------------------------------------------------------------|
| Provedor de E-mail   | Envia código de 2FA, link de recuperação de senha, convites de acesso |
| JWT                  | Geração de token de autenticação e refresh                            |

- A comunicação com o provedor de e-mail ocorre via **SMTP** ou serviços como **SendGrid** ou **Amazon SES**.
- Os tokens JWT são assinalados com chaves seguras e validados em cada requisição autenticada.

