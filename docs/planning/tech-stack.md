# Stack Tecnológica do Projeto

## Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 30/05/2025 | 0.1    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton)    |
| 05/06/2025 | 1.0    | Adiciona tecnologias do projeto | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 05/06/2025 | 2.0    | Aprimora descrição do documento | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 06/06/2025 | 2.1    | Adiciona ferramentas de documentação | [Maelton Lima dos Santos](https://github.com/Maelton) |

## Descrição

Este documento descreve o conjunto de tecnologias adotadas para o desenvolvimento do sistema **BRISA Helpdesk**.

## Tecnologias Utilizadas

### Frontend

- **Framework:** [Next.js](https://nextjs.org/)
- **Linguagem:** TypeScript
- **Versão do Node.js:** 22.16.0 (LTS)
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
- **Versão do Node.js:** 22.16.0 (LTS)
- **API:** RESTful com suporte à autenticação JWT + 2FA
- **Validação:** Class-validator / class-transformer
- **Segurança:** Helmet, bcrypt, CORS, Rate Limiting
- **Documentação:** Swagger
- **Exportação de arquivos:** PDFKit (ou Puppeteer)
- **Emails:** [Nodemailer](https://nodemailer.com/) e [Ethereal Email](https://ethereal.email/)
- **Gerenciador de pacotes:** [pnpm](https://pnpm.io/)

### Banco de Dados

- **Banco:** PostgreSQL (versão 16.9)
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

### Documentação

- **Plataforma de publicação:** [GitHub Pages](https://pages.github.com/)
- **Gerador de documentação:** [MkDocs](https://www.mkdocs.org/)
- **Tema recomendado:** [`mkdocs-material`](https://squidfunk.github.io/mkdocs-material/)
- **Objetivo:** Disponibilizar a documentação do projeto de forma versionada, acessível e responsiva, com renderização otimizada para Markdown.

---

## Considerações

A stack escolhida visa atender os requisitos de desempenho, segurança, escalabilidade, rastreabilidade, integração via APIs, responsividade e manutenção a longo prazo.
