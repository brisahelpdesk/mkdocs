# PROJETO DE IMERSÃO

**PARCEIRO DO PROGRAMA DE RESIDÊNCIA EM TIC:** ESCOLA  
**NOME DO PROJETO:** Sistema de Suporte a Chamados  
**EMPRESA PROPONENTE DO PROJETO:** ---  
**CONTATO NA EMPRESA:** ---  
**E-MAIL:** ---  
**Professor Orientador:** Rian  
**Grupo:** 9  

---

## DESCRIÇÃO DO PROJETO PROPOSTO

O sistema de chamados será uma ferramenta para gerenciar solicitações e atendimentos relacionados a produtos ou serviços, com funcionalidades essenciais para:

- Cadastro de produtos  
- Abertura e consulta de tickets  
- Acompanhamento de SLA (Service Level Agreement)  
- Comunicação com usuários por e-mail  

---

## REQUISITOS FUNCIONAIS

### Perfis de Acesso

- **Administrador**: acesso total ao sistema, gerenciamento de usuários, SLAs, tipos de chamados e relatórios.  
- **Supervisor/Gerente**: visualização e acompanhamento dos chamados da equipe, geração de relatórios e reatribuição de chamados.  
- **Atendente/Suporte**: visualização e gestão dos chamados atribuídos, inclusão de observações e encerramento.  
- **Solicitante/Cliente**: criação de chamados, acompanhamento do status, comunicação via chat e avaliação de atendimento.  

### Tipos de Chamados

- Incidente  
- Requisição de Serviço  
- Dúvida  
- Melhoria  
- Outros (personalizável pelo Admin)  

### Tipos de SLA

- Padrão (ex: 8h úteis)  
- Crítico (ex: 2h corridas)  
- Agendado (ex: atendimento marcado)  
- Customizável por cliente, tipo de chamado ou contrato  

### Tipos de Atendimento

- Remoto  
- Presencial  
- Telefônico  
- Chat interno (com histórico)  
- Automático (por bots ou scripts integrados)  

### Responsividade

- Interface responsiva para desktop, tablets e celulares  
- Compatível com navegadores Chrome, Firefox, Edge e Safari  

### Controle de Horas por Chamado

- Registro de tempo dedicado por técnico  
- Pausa e retorno no atendimento (cronômetro)  
- Histórico de tempo gasto por interação  
- Totalizador por chamado, cliente, técnico e mês  

### Status de Atendimento

- Novo  
- Em andamento  
- Aguardando cliente  
- Aguardando terceiros  
- Resolvido  
- Reaberto  
- Cancelado  
- Encerrado  

### Comunicação e Notificações

- Notificações por e-mail e/ou push  
- Comentários internos e externos (público e privado)  
- Integração com WhatsApp e e-mail (opcional)  

### Dashboards e Relatórios

- Visão geral por status, SLA, tipo e técnico  
- Exportação em PDF/Excel  
- Indicadores: tempo médio de resolução, SLAs violados, chamados por técnico etc.  

### Busca e Filtros Avançados

- Filtro por número do chamado, cliente, data, técnico, status etc.  
- Salvamento de filtros frequentes  

### Avaliação de Atendimento

- Feedback do cliente ao encerrar o chamado  
- Nota e comentário  
- Relatório de satisfação  

### Base de Conhecimento

- Artigos e tutoriais internos  
- Sugestão automática ao abrir chamado  
- Acesso controlado por perfil  

### Integrações (opcional)

- API REST (ERP, CRM etc.)  
- Webhooks  
- Integração com AD/LDAP para login  

### Inclusão de Anexos

- Abertura: solicitante pode anexar arquivos  
- Atendimento: anexos por técnicos e solicitantes  
- Limite por chamado: configurável (ex: 10 arquivos)  
- Tamanho máximo por arquivo: 20MB  
- Tipos permitidos:  
  - Imagens: .jpg, .jpeg, .png, .gif, .bmp  
  - Documentos: .pdf, .doc, .docx, .xls, .xlsx, .txt  
  - Compactados: .zip, .rar  
  - Outros: configurável pelo administrador  

---

## REQUISITOS NÃO-FUNCIONAIS

1. **Desempenho**: Tela inicial deve carregar em até 3 segundos  
2. **Segurança**:  
   - Login/senha + 2FA  
   - Permissões baseadas em perfis  
   - Criptografia de dados sensíveis  
3. **Disponibilidade**: 99,5% de uptime mensal  
4. **Escalabilidade**: Suportar crescimento sem perda de desempenho  
5. **Backup**: Diário com retenção de 30 dias  
6. **Logs de Auditoria**: Registro de ações críticas  

---

## CRITÉRIOS DE ACEITAÇÃO

### Funcionalidade

1. Chamados podem ser criados, visualizados, editados e encerrados por diferentes perfis  
2. Tipos de chamados, SLAs e atendimentos configuráveis  
3. Controle de tempo total e por interação  
4. Anexos seguros em qualquer fase  
5. Status atualizados corretamente  
6. Painel e relatórios com dados atualizados  
7. Comunicação via comentários durante o ciclo do chamado  

### Usabilidade e Interface

1. Responsivo para mobile e tablets  
2. Interface com fácil navegação, busca e filtros  
3. Abertura de chamado intuitiva com sugestões automáticas  
4. Notificações via e-mail ou push  

### Testes e Qualidade

1. 100% dos requisitos cobertos por testes  
2. Chamados em diferentes fluxos funcionam corretamente  
3. Bugs críticos resolvidos antes da entrega  
4. Cliente aprovou homologação em ambiente de testes  

### Documentação e Entregáveis

1. Documentação técnica e manual de usuário atualizados  
2. Scripts de deploy e instruções entregues  
3. Ambiente de produção configurado e testado  

---
