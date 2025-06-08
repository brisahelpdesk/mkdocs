# Arquitetura de Sistema

## 1. Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 08/06/2025 | 0.1    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 08/06/2025 | 0.2    | Adiciona diagrama de arquitetura | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 08/06/2025 | 0.5    | Adiciona referencia aos módulos backend | [Maelton Lima dos Santos](https://github.com/Maelton) |

## 2. Visão Geral

O sistema adota uma **arquitetura modular monolítica** baseada em **NestJS (backend)** e **Next.js (frontend)**, com PostgreSQL como banco de dados relacional e armazenamento externo de arquivos (ex: AWS S3) para anexos. A comunicação entre frontend e backend ocorre por meio de uma **API RESTful segura**, utilizando autenticação JWT com suporte a 2FA.

## 3. Diagrama de Arquitetura do Sistema

[![](./images/system-architecture.drawio.svg)](./images/system-architecture.drawio.svg)

### 3.1 Módulos Backend 
- [**AuthModule**](./modules/auth-module.md): autenticação, cadastro de usuários, 2FA
- [**TicketModule**](./modules/ticket-module.md): abertura, consulta e interações de chamados
- [**AssignmentModule**](./modules/assignment-module.md): atribuição automática de chamados
- [**KnowledgeBaseModule**](./modules/knowledge-base-module.md): artigos, fluxo de aprovação, sugestões por palavra-chave
- [**SelfServiceModule**](./modules/selfservice-module.md): chamados gerados automaticamente por acesso à base de conhecimento
- [**SlaModule**](./modules/sla-module.md): controle de SLA e monitoramento de prazos
- [**TimerModule**](./modules/timer-module.md): cronômetro por interação ou técnico
- [**ContractModule**](./modules/contract-module.md): validação de cobertura por cliente/produto
- [**ReportModule**](./modules/report-module.md): geração de relatórios em PDF/Excel
- [**NotificationModule**](./modules/notification-module.md): notificações por e-mail e push
- [**AuditModule**](./modules/audit-module.md): registro de ações críticas
- [**DashboardModule**](./modules/dashboard-module.md): indicadores gráficos e filtros

<!-- ## 4. Modelo Entidade Relacionamento -->

<!-- ## 5. Diagrama de Classes -->
