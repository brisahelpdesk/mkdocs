# ChatModule (Módulo de Chat em Tempo Real)

O `ChatModule` provê a funcionalidade de comunicação em tempo real entre os usuários do sistema, permitindo a troca de mensagens instantâneas durante o atendimento de chamados. Ele utiliza WebSockets via `socket.io` para garantir latência mínima e experiência fluida de conversa.

---

## Objetivo Principal

Facilitar a comunicação direta e instantânea entre solicitantes e técnicos/supervisores durante o processo de atendimento de chamados técnicos.

---

## O que o ChatModule faz

| Função                            | Descrição                                                                    |
| --------------------------------- | ---------------------------------------------------------------------------- |
| Canal de chat por chamado         | Cria salas de chat específicas para cada chamado em aberto                   |
| Envio e recebimento em tempo real | Utiliza `WebSocket` via `socket.io` para troca imediata de mensagens         |
| Histórico de mensagens            | Armazena conversas para posterior consulta e auditoria                       |
| Notificações por nova mensagem    | Integra com o `NotificationModule` para alertar usuários fora da conversa    |
| Suporte a mensagens com anexos    | Permite enviar arquivos leves (imagens, PDFs, etc.) via link do Object Store |
