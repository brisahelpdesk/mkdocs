# Cronograma de Implementação (Projeto Backend)

## Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 14/07/2025 | 0.1    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 14/07/2025 | 0.2    | Adiciona EAP do projeto backend | [Maelton Lima dos Santos](https://github.com/Maelton) |

## Introdução

A ordem de implementação dos módulos do backend foi definida com base nas dependências técnicas identificadas nas interfaces do sistema e nas necessidades de negócio descritas na documentação. O objetivo é garantir que cada módulo fundamental esteja disponível antes dos módulos que dele dependem, otimizando o fluxo de desenvolvimento e reduzindo retrabalho.

## Critérios Utilizados

- **Dependências Técnicas**: Módulos que fornecem entidades ou serviços essenciais (ex: usuários, autenticação, produtos) devem ser implementados antes dos módulos consumidores (ex: tickets, contratos, autoatendimento).

- **Fluxo de Negócio**: A sequência respeita o ciclo natural de uso do sistema, desde o cadastro e autenticação de usuários até a geração de relatórios e dashboards.

- **Modularidade e Testabilidade**: Implementar primeiro módulos independentes ou de baixa dependência facilita testes unitários e integração incremental.

- **Reutilização e Integração**: Módulos centrais (ex: User, Auth, Product) são base para múltiplos outros, maximizando o reaproveitamento de código e lógica.

## Ordem de Implementação dos Módulos e Dependências

### Núcleo & Fundamentos

#### 1. UserModule
Base para autenticação, permissões, abertura de chamados, atribuição de técnicos, notificações e auditoria. Sem usuários, não há como operar o sistema.

#### 2. AuthModule
Depende do UserModule para autenticação e controle de acesso. Essencial para proteger os demais módulos e garantir segurança desde o início.

#### 3. NotificationModule
Independente, mas fundamental para eventos de tickets, usuários e outros módulos para informar usuários sobre atualizações e prazos.

---

### Catálogo & Contratos

#### 4. ProductModule
Necessário para contratos e para vincular produtos/serviços aos chamados. Sem produtos, não há como definir escopo de atendimento.

#### 5. ContractModule
Depende de usuários (clientes) e produtos. Define regras contratuais que impactam diretamente a abertura de chamados e aplicação de SLA.

---

### Base de Conhecimento

#### 6. KnowledgeBaseModule
Independente, mas fundamental para autoatendimento e para alimentar informações em chamados e feedbacks.

---

### Operação de Chamados

#### 7. SlaModule
Independente, mas fundamental para aplicar e monitorar acordos de nível de serviço nos chamados. Pode se relacionar com os módulos de contratos, produtos e clientes.

#### 8. TimerModule
Independente, mas fundamental para registrar o tempo de atendimento, essencial para relatórios e SLAs.

#### 9. ChatModule
Independente, mas fundamental para permitir comunicação em tempo real durante o atendimento.

#### 10. TicketModule
Núcleo operacional do sistema. Depende de usuários, contratos, produtos, SLAs, TimerModule e ChatModule para funcionar corretamente. Utiliza os módulos de controle de tempo e gerenciamento de chats de conversa.

#### 11. AssignmentModule
Depende de tickets e usuários (técnicos) para distribuir chamados automaticamente.

---

### Autoatendimento & Feedback

#### 12. SelfServiceModule
Depende da base de conhecimento, usuários e tickets para registrar e converter interações de autoatendimento.

#### 13. FeedbackModule
Depende de tickets, usuários e artigos da base de conhecimento para coletar avaliações e alimentar relatórios.

---

### Monitoramento & Gestão

#### 14. AuditModule
Depende de eventos realizados pelos usuários em de todos os módulos para registrar ações críticas e garantir rastreabilidade.

#### 15. ReportModule
Depende de dados de tickets, timer, feedback, SLA, etc., para gerar relatórios gerenciais e operacionais.

#### 16. DashboardModule
Depende de dados consolidados de tickets, timer, feedback, SLA, etc., para exibir indicadores em tempo real.

## Estrutura Analítica do Projeto (Projeto Backend)

[![](./images/backend-implementation-wbs.drawio.svg)](./images/backend-implementation-wbs.drawio.svg)

<!-- ## Gráfico de Gantt (Projeto Backend) -->

## Conclusão

A ordem proposta visa garantir que cada etapa do desenvolvimento seja sustentada por uma base sólida, respeitando as dependências técnicas e o fluxo de valor do negócio. Isso facilita a integração contínua, a validação incremental e a entrega de valor ao usuário final desde as primeiras sprints.