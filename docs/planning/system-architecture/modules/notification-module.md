# NotificationModule (Módulo de Notificações)

O `NotificationModule` é responsável por enviar mensagens automáticas aos usuários sempre que ocorrem eventos relevantes no sistema, como abertura, atualização ou encerramento de chamados. Ele centraliza o envio de notificações por e-mail ou outros canais, garantindo que os usuários estejam sempre informados.

---

## Objetivo Principal

Manter os usuários atualizados em tempo real sobre os eventos do sistema, por meio de notificações enviadas automaticamente via e-mail ou outros canais integrados.

---

## O que o NotificationModule faz

| Função                               | Descrição                                                                 |
|-------------------------------------|---------------------------------------------------------------------------|
| Envia notificações por e-mail       | Informa o solicitante e/ou técnico sobre abertura, atualização e conclusão de chamados |
| Suporte a múltiplos perfis          | Diferentes mensagens para CLI, ATD, SUP, ADM                             |
| Templates personalizáveis           | Estrutura padronizada para corpo do e-mail (HTML ou texto)               |
| Gerencia preferências do usuário    | (opcional) Permite configurar quais notificações o usuário deseja receber |
| Emissão de alertas e lembretes      | Pode ser utilizado para enviar lembretes de prazo, vencimentos, etc.    |

---

## Relacionamento com Serviços Externos

| Serviço               | Papel                                                                          |
|-----------------------|--------------------------------------------------------------------------------|
| Provedor de E-mail    | Responsável pelo envio das mensagens (SMTP, SendGrid, Amazon SES, etc.)        |
| Webhook (opcional)    | Pode ser utilizado para integrar com sistemas externos que precisam ser notificados |
