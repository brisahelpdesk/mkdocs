# Arquitetura de Sistema

## 1. Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 08/06/2025 | 0.1    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 08/06/2025 | 0.2    | Adiciona diagrama de arquitetura | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 08/06/2025 | 0.5    | Adiciona referencia aos módulos backend | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 22/06/2025 | 0.6    | Adiciona arquitetura de software backend | [Maelton Lima dos Santos](https://github.com/Maelton) |

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

## 4. Arquitetura de Software (Backend)

### 4.1 Visão Geral

O backend do sistema BRISA Helpdesk seguirá o padrão arquitetural **Layered Architecture** (Arquitetura em Camadas), conforme descrito no livro ["Software Architecture Patterns" (O'Reilly)](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch01.html).

### 4.2 Diagrama de Arquitetura de Software (Backend)

[![](./images/backend-software-architecture.drawio.svg)](./images/backend-software-architecture.drawio.svg)

### 4.3 Camadas da Arquitetura

Esta abordagem organiza o código em quatro camadas principais, cada uma com responsabilidades bem definidas e limites claros.

| Camada | Responsabilidades Principais | Exemplos |
| - | - | - |
| **Presentation Layer** | Lida com entrada/saída de dados, recebe requisições HTTP, valida dados, mapeia DTOs e delega para a camada de negócio.       | `user.controller.ts`, `user-create-update.dto.ts` |
| **Business Layer**     | Contém a lógica de negócio central do sistema, orquestrando regras, fluxos e validações complexas.                           | `user.service.ts`, `user-not-found.exception.ts` |
| **Persistence Layer**  | É o código da sua aplicação que se comunica com o Database Layer. É responsável por consultar, salvar, atualizar e deletar dados, independentemente de qual tecnologia de banco está por trás (ORM, JDBC, Prisma, etc.). | `user.repository.ts`, `prisma.service.ts` |
| **Database Layer**     | Infraestrutura de armazenamento físico e persistente. Inclui bancos de dados relacionais (PostgreSQL), não relacionais (Redis) e armazenamentos de objetos (ex.: Firebase Storage, AWS S3). | PostgreSQL, Redis, Firebase |

<!-- ## 5. Modelo Entidade Relacionamento -->

<!-- ## 6. Diagrama de Classes -->
