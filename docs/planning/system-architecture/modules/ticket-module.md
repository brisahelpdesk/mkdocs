# TicketModule (Módulo de Chamados)

O `TicketModule` é o núcleo do sistema BRISA Helpdesk. Ele gerencia todo o ciclo de vida dos chamados técnicos — desde a abertura até a conclusão — registrando interações, controlando status e garantindo o histórico completo do atendimento. Também é responsável por permitir o envio e acesso a anexos relacionados aos chamados.

---

## Objetivo Principal

Permitir que clientes abram chamados para relatar problemas ou dúvidas, que técnicos interajam com o cliente ao longo do atendimento e que supervisores acompanhem o histórico e o progresso dos chamados em tempo real.

---

## O que o TicketModule faz

| Função                              | Descrição                                                                 |
|------------------------------------|--------------------------------------------------------------------------|
| Abertura de chamados               | Permite que o cliente registre um chamado descrevendo seu problema       |
| Registro de interações             | Técnicos e clientes podem trocar mensagens e atualizações dentro do chamado |
| Upload e visualização de anexos    | Permite anexar arquivos relacionados ao chamado ou às interações         |
| Controle de status                 | Define e atualiza status como “Novo”, “Em atendimento”, “Aguardando cliente”, “Encerrado” etc. |
| Histórico completo do chamado      | Armazena todas as ações e interações realizadas                          |
| Reatribuição manual de técnico     | Supervisores podem alterar o técnico responsável                         |
| Geração de eventos                 | Dispara notificações e atualizações em tempo real                        |

---

## Relacionamento com Serviços Externos

| Serviço               | Papel                                                                           |
|-----------------------|---------------------------------------------------------------------------------|
| Object Storage (S3/Firebase) | Armazenamento de arquivos anexados aos chamados ou interações            |
| WebSocket (opcional) | Emissão de atualizações em tempo real sobre o progresso do chamado              |
