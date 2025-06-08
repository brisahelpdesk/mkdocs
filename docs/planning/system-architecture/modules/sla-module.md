# SlaModule (Módulo de Acordo de Nível de Serviço)

O `SlaModule` é responsável por calcular, monitorar e evidenciar o cumprimento dos Acordos de Nível de Serviço (SLAs) definidos para cada chamado, com base em regras de contrato, tipo de chamado e prioridade. Ele atua como componente fundamental para garantir que o atendimento ocorra dentro dos prazos acordados.

---

## Objetivo Principal

Controlar os prazos de atendimento conforme os contratos firmados, alertando sobre possíveis violações de SLA e fornecendo indicadores de desempenho aos supervisores.

---

## O que o SlaModule faz

| Função                          | Descrição                                                                 |
|--------------------------------|--------------------------------------------------------------------------|
| Aplica SLA ao abrir chamado    | Define automaticamente o SLA com base no contrato, tipo e prioridade     |
| Calcula tempo restante         | Monitora o tempo restante para atendimento/resolução                     |
| Identifica violações           | Detecta automaticamente SLAs ultrapassados e marca o chamado             |
| Exibe SLA nos detalhes do chamado | Informa o tipo de SLA e status (em andamento, violado, etc.)           |
| Gera alertas ou destaques visuais | Pode enviar notificações ou destacar chamados críticos na interface    |
| Alimenta indicadores gerenciais | Fornece dados para dashboards e relatórios                              |
