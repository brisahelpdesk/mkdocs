# Stack de Desenvolvimento - Sistema de Suporte a Chamados

Este documento descreve a stack de tecnologias adotada para o desenvolvimento do Sistema de Suporte a Chamados, conforme os requisitos levantados.

## Tecnologias Utilizadas

### Frontend

- **Framework:** [Next.js](https://nextjs.org/)
- **Linguagem:** TypeScript
- **Estilização:** Tailwind CSS
- **Biblioteca de UI:** [shadcn/ui](https://ui.shadcn.com/)
- **Gerenciamento de Estado:** Zustand (ou Redux Toolkit, conforme necessidade)
- **Testes:** Vitest (testes de unidade e integração)
- **Gerenciamento de formulários:** React Hook Form
- **WebSockets:** [socket.io-client](https://www.npmjs.com/package/socket.io-client) (para chat, notificações e reatribuição de chamados)
- **Gerenciador de pacotes:** [pnpm](https://pnpm.io/)

### Backend

- **Framework:** [NestJS](https://nestjs.com/)
- **Linguagem:** TypeScript
- **API:** RESTful com suporte à autenticação JWT + 2FA
- **Validação:** Class-validator / class-transformer
- **Segurança:** Helmet, bcrypt, CORS, Rate Limiting
- **Documentação:** Swagger
- **Exportação de arquivos:** PDFKit (ou Puppeteer)
- **Emails:** [Nodemailer](https://nodemailer.com/) e [Ethereal Email](https://ethereal.email/)
- **Gerenciador de pacotes:** [pnpm](https://pnpm.io/)

### Banco de Dados

- **Banco:** PostgreSQL
- **ORM:** Prisma

### Autenticação e Autorização

- JWT (JSON Web Token)
- 2FA (Two-Factor Authentication)
- Controle de acesso por perfil (Admin, Gerente, Atendente, Cliente)

### Armazenamento de Arquivos

- AWS S3 ou Firebase Storage (para arquivos de até 20MB por anexo)

### Testes

- Backend: Jest + Supertest
- Frontend: Vitest (testes de unidade e integração)

### DevOps e Infraestrutura

- **Containers:** Docker
- **CI/CD:** GitHub Actions
- **Monitoramento:** UptimeRobot, LogRocket (frontend), Prometheus (backend)
- **Deploy:** Netlify, Render, Railway, DigitalOcean ou AWS EC2

---

## Considerações

A stack escolhida visa atender os requisitos de desempenho, segurança, escalabilidade, rastreabilidade, integração via APIs, responsividade e manutenção a longo prazo.
