# Dúvidas sobre o Sistema de Suporte a Chamados

## CLIENTE

### Informações Relevantes para Armazenamento

Além de nome e e-mail, os seguintes campos serão armazenados:

- **CNPJ/CPF:** Obrigatório para identificação fiscal e legal.
- **Razão Social / Nome Fantasia:** Para distinguir nome jurídico e comercial.
- **Telefone Principal:** Para contato direto e emergencial.
- **Endereço Completo:** Para atendimentos presenciais e correspondências.
- **Setor/Segmento de Atuação:** Para personalização de SLAs e atendimento especializado.
- **Porte da Empresa:** Micro, pequena, média ou grande (influencia SLA e priorização).
- **Data de Contratação:** Para controle de antiguidade e histórico.
- **Status:** Ativo, inativo, suspenso.
- **Observações Especiais:** Particularidades do cliente.

### Vínculo Pessoa Física x Jurídica

- O sistema deve suportar **tanto Pessoa Jurídica (CNPJ) quanto Pessoa Física (CPF)**.
- Campo discriminador: **tipo_pessoa (PF/PJ)**.
- **Validações diferentes** para cada tipo de documento.

### Cliente vs Solicitante

- **Não são sinônimos:**
  - **Cliente:** Entidade contratante (empresa ou pessoa que paga pelo serviço).
  - **Solicitante:** Usuário final que abre o chamado (funcionário da empresa cliente).
- **Relacionamento:** Um cliente pode ter vários solicitantes.

---

## COLABORADOR

### Atendente vs Suporte

- São considerados **sinônimos no contexto operacional**.
- No sistema, utilizar um **perfil único: "Técnico de Suporte"**.
- Caso haja necessidade, o sistema pode diferenciar por **nível de experiência (Júnior/Pleno/Sênior)**.

### Informações Relevantes para Armazenamento

- **Matrícula/Código do Funcionário**
- **Departamento/Setor**
- **Cargo/Função**
- **Supervisor Direto**
- **Filial/Localização**
- **Telefone Corporativo/Ramal**
- **Especialidades**
- **Nível de Acesso**
- **Horário de Trabalho**
- **Status:** Ativo, férias, licença, desligado.

### Múltiplas Funções por Colaborador

- **Sim, será permitido.**
- Sistema deve permitir **perfis múltiplos por usuário**.
- Exemplo: João Silva pode atuar como **Técnico** e **Supervisor**.
- Interface e permissões devem ser ajustáveis conforme o **perfil ativo na sessão**.
- O sistema manterá **log de auditoria** para rastreamento de ações por perfil.

---

## CONTRATO

### Produtos/Serviços por Contrato

- Modelo recomendado: **Contrato Mestre com Múltiplos Itens**.
- Um contrato pode conter **vários produtos ou serviços**.

### Inclusão de Novos Produtos/Serviços

- Preferencialmente via **Aditivo Contratual**, mantendo o histórico unificado.
- Novo contrato só em caso de **mudança significativa de escopo**.

### Informações Relevantes do Contrato

- **Número do Contrato:** Exemplo: BRISA-2025-001.
- **Data de Assinatura**
- **Vigência (Início e Fim)**
- **Valor Total**
- **Modalidade:** Suporte, licenciamento, desenvolvimento.
- **SLA Contratual**
- **Cláusulas Especiais**
- **Status:** Ativo, suspenso, encerrado, renovação.

---

## SLA

### Calendários de Atendimento

- **ALTAMENTE RECOMENDADO** implementar diferentes **calendários de SLA**, por exemplo:

| Calendário | Horário |
| --------- | ----- |
| Comercial | Segunda a sexta, 8h às 18h |
| Comercial Estendido | Segunda a sexta, 8h às 18h + Sábado, 8h às 12h |
| 24x5 | Segunda a sexta, 24 horas |
| 24x7 | Todos os dias, 24 horas |
| Personalizado | Configurável por cliente |

### Funcionalidades necessárias para SLA:

- Consideração de **feriados nacionais e regionais**.
- Configuração de **exceções pontuais** (ex: manutenções).
- **Cálculo automático** de prazos com base no calendário ativo.

---

## Sistema de Autenticação e Perfis

### Autenticação de Dois Fatores

- **Dúvida:** A autenticação em dois fatores (2FA) deve ser aplicada a todos os usuários ou apenas colaboradores?
- **Resposta:** Ficou definido que, por ora, o sistema seguirá com um **usuário ADMIN para cadastro e permissões**. Não foi detalhado se o 2FA será para todos ou apenas para colaboradores. (Essa questão pode ser definida em fases posteriores.)

### Sistema de Usuário e Senha

- **Autenticação básica com controle de senha:**
  - **Login:** E-mail ou username.
  - **Política de Senhas Recomendada:**
    - Mínimo de 8 caracteres.
    - Pelo menos 1 maiúscula, 1 minúscula e 1 número.
    - Renovação a cada 90 dias (opcional).
    - Proibição de reutilizar as 3 últimas senhas.

- **Funcionalidades de Segurança Adicionais:**
  - Bloqueio após 5 tentativas de login incorretas.
  - Recuperação de senha por e-mail.
  - Logout automático por inatividade.
  - Controle de sessões simultâneas.

---

## Considerações Finais

- Em relação ao **protótipo**, a resposta geral da equipe foi: **"Está OK. Está muito bom."**
- O sistema continuará a ser desenvolvido considerando as decisões descritas aqui e nas respostas do primeiro questionário.

