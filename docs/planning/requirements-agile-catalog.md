# Catálogo de Requisitos Ágeis 

## 1. Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 06/05/2025 | 0.1    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 06/05/2025 | 0.2    | Descreve requisitos        | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 06/05/2025 | 0.3    | Adiciona histórias 7 a 16  | [Maelton Lima dos Santos](https://github.com/Maelton) |
| 06/06/2025 | 0.5    | Adiciona história US017    | [Maelton Lima dos Santos](https://github.com/Maelton) |

---

## 2. Personas

| ID   | Persona      | Descrição                                                                            |
|------|--------------|--------------------------------------------------------------------------------------|
| ADM  | Administrador | Gerencia configurações, usuários, artigos e parâmetros do sistema.                  |
| SUP  | Supervisor    | Acompanha chamados da equipe, reatribui e aprova artigos da base de conhecimento.   |
| ATD  | Atendente     | Recebe e resolve chamados; pode sugerir conteúdos para a base.                      |
| CLI  | Solicitante   | Cliente que abre chamados e consulta seu status.                                    |
| VIS  | Visitante     | Usuário sem login que pode consultar a base pública de conhecimento (se permitido). |

---

## 3. Histórias de Usuário (Requisitos Funcionais)

### 3.1 Overview das Histórias de Usuário (Ordenadas por Execução)

| ID    | Título                                      | Descrição                                                                     | Dependência  |
| ----- | ------------------------------------------- | ----------------------------------------------------------------------------- | ------------ |
| US001 | Abertura de chamado técnico                 | Permitir que o solicitante crie chamados com anexos e tipo definido.          | RT001        |
| US003 | Consulta de status do chamado               | Exibir o andamento, histórico e anexos de um chamado.                         | US001        |
| US002 | Atribuição automática de chamado            | Distribuir chamados automaticamente para técnicos com menor carga.            | US001        |
| US004 | Sugestão automática da base de conhecimento | Sugerir artigos da base ao abrir chamado conforme palavras-chave.             | US001, RT004 |
| US005 | Registro de autoatendimento como chamado    | Gerar automaticamente um chamado ao consultar artigo da base de conhecimento. | US004        |
| US006 | Controle de tempo por atendimento           | Permitir que o técnico registre o tempo gasto em cada atendimento.            | US002        |
| US007 | Cadastro de produtos e serviços             | Permitir que o administrador gerencie o catálogo de produtos e serviços.      | -            |
| US008 | Cadastro de pessoas físicas e jurídicas     | Permitir que o administrador registre clientes e empresas no sistema.         | -            |
| US009 | Cadastro de usuários do sistema             | Permitir que o administrador crie e edite acessos dos usuários.               | RT001        |
| US010 | Visualizar produtos e serviços vinculados   | Permitir que o cliente veja os produtos/serviços que tem acesso.              | US007, US008 |
| US011 | Notificações por e-mail                     | Enviar notificações sobre atualizações dos chamados aos usuários.             | US001        |
| US012 | Avaliação de atendimento                    | Permitir que o cliente avalie o atendimento após encerramento.                | US003        |
| US013 | Visualização de dashboards                  | Apresentar indicadores e relatórios para monitoramento de desempenho.         | US006        |
| US014 | Gerenciar base de conhecimento              | Permitir que perfis autorizados criem e mantenham artigos técnicos.           | US004        |
| US015 | Gerenciamento de contratos de serviço       | Permitir controle de escopo de atendimento por contrato.                      | US007, US008 |
| US016 | Visualização de SLA dos chamados            | Exibir o SLA de cada chamado no detalhe para clientes e supervisores.         | US003        |
| US017 | Geração e download de relatórios gerenciais | Permitir geração e exportação de relatórios filtráveis em PDF e Excel. | US013, RT006 |

---

### 3.2 Histórias de Usuário Detalhadas (Ordenadas por ID)

#### ID: US001  
**Título:** Abertura de chamado técnico  
**Persona:** CLI  
**História:**  
Como solicitante, quero abrir um chamado descrevendo meu problema, para receber suporte técnico.  
**Critérios de Aceitação:**  
- Deve permitir seleção do tipo de chamado (Incidente, Dúvida, etc.)  
- Deve permitir adicionar anexos (.pdf, .docx, .jpg, etc.)  
- Deve notificar o solicitante e o técnico automaticamente após a abertura  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** RT001  

---

#### ID: US002  
**Título:** Atribuição automática de chamado  
**Persona:** SUP  
**História:**  
Como sistema, quero atribuir chamados automaticamente ao técnico com menor carga, para balancear a distribuição de trabalho.  
**Critérios de Aceitação:**  
- Deve considerar apenas técnicos ativos e habilitados  
- Em caso de empate, deve atribuir de forma aleatória  
- Supervisores podem reatribuir manualmente  
**Prioridade:** Alta  
**Dificuldade:** Alta  
**Dependência:** US001  

---

#### ID: US003  
**Título:** Consulta de status do chamado  
**Persona:** CLI  
**História:**  
Como solicitante, quero consultar o status do meu chamado, para acompanhar seu progresso.  
**Critérios de Aceitação:**  
- Deve exibir status atual (Ex: Em andamento, Aguardando cliente)  
- Deve mostrar histórico de interações  
- Deve permitir visualização de anexos trocados  
**Prioridade:** Alta  
**Dificuldade:** Baixa  
**Dependência:** US001  

---

#### ID: US004  
**Título:** Sugestão automática da base de conhecimento  
**Persona:** CLI  
**História:**  
Como solicitante, quero receber sugestões de artigos ao abrir um chamado, para tentar resolver por conta própria.  
**Critérios de Aceitação:**  
- Sugestões com base em palavras-chave digitadas  
- Artigos ordenados por relevância e avaliação de utilidade  
- Permite avaliar se o artigo ajudou  
**Prioridade:** Alta  
**Dificuldade:** Alta  
**Dependência:** US001, RT004  

---

#### ID: US005  
**Título:** Registro de autoatendimento como chamado  
**Persona:** CLI  
**História:**  
Como sistema, quero registrar acessos à base de conhecimento como chamados do tipo Autoatendimento, para manter controle das interações.  
**Critérios de Aceitação:**  
- Chamado gerado automaticamente com status "Em Consulta"  
- Se resolvido, marcado como "Resolvido – Autoatendimento"  
- Se não resolvido, pode ser convertido em chamado técnico  
**Prioridade:** Média  
**Dificuldade:** Média  
**Dependência:** US004  

---

#### ID: US006  
**Título:** Controle de tempo por atendimento  
**Persona:** ATD  
**História:**  
Como técnico, quero iniciar, pausar e finalizar um cronômetro durante o atendimento, para registrar o tempo gasto.  
**Critérios de Aceitação:**  
- Deve exibir tempo por interação e tempo total do chamado  
- Deve permitir retomar o cronômetro  
- Deve exportar dados para relatórios  
**Prioridade:** Alta  
**Dificuldade:** Alta  
**Dependência:** US002  

---

#### ID: US007  
**Título:** Cadastro de produtos e serviços  
**Persona:** ADM  
**História:**  
Como administrador, quero cadastrar produtos e serviços oferecidos pela empresa, para que possam ser vinculados aos chamados e contratos.  
**Critérios de Aceitação:**  
- Deve permitir criação, edição e exclusão de produtos/serviços  
- Deve permitir ativar/desativar itens sem removê-los do histórico  
- Itens devem poder ser associados a contratos e chamados  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** -  

---

#### ID: US008  
**Título:** Cadastro de pessoas físicas e jurídicas  
**Persona:** ADM  
**História:**  
Como administrador, quero cadastrar pessoas físicas e jurídicas, para gerenciar clientes/colaboradores.  
**Critérios de Aceitação:**  
- Deve diferenciar cadastro de PF e PJ  
- Deve permitir associar pessoas a contratos e produtos  
- Deve validar CPF/CNPJ  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** -  

---

#### ID: US009  
**Título:** Cadastro de usuários do sistema  
**Persona:** ADM  
**História:**  
Como administrador, quero cadastrar e configurar os usuários que acessam o sistema, para controlar os perfis e permissões.  
**Critérios de Aceitação:**  
- Deve permitir definir perfil de acesso (ADM, SUP, ATD, CLI)  
- Deve enviar convite com link de ativação  
- Deve permitir desativar usuários sem excluí-los  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** RT001  

---

#### ID: US010  
**Título:** Visualizar produtos e serviços vinculados  
**Persona:** CLI  
**História:**  
Como cliente, quero visualizar os produtos e serviços contratados, para acompanhar quais itens estão cobertos pelo suporte.  
**Critérios de Aceitação:**  
- Deve exibir nome, categoria e status do produto  
- Deve listar contratos vinculados e tipos de chamados cobertos  
**Prioridade:** Média  
**Dificuldade:** Baixa  
**Dependência:** US007, US008  

---

#### ID: US011  
**Título:** Notificações por e-mail  
**Persona:** CLI, ATD  
**História:**  
Como usuário, quero receber notificações por e-mail quando o status do chamado for alterado, para me manter informado.  
**Critérios de Aceitação:**  
- Deve enviar e-mail ao abrir, atualizar ou encerrar chamados  
- Deve permitir configurar preferências de notificação  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** US001  

---

#### ID: US012  
**Título:** Avaliação de atendimento  
**Persona:** CLI  
**História:**  
Como cliente, quero avaliar o atendimento recebido, para que a empresa possa melhorar seus serviços.  
**Critérios de Aceitação:**  
- Deve solicitar avaliação ao encerrar chamado  
- Deve permitir nota de 1 a 5 estrelas e comentário opcional  
- Avaliações devem ser visíveis para supervisores  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** US003  

---

#### ID: US013  
**Título:** Visualização de dashboards  
**Persona:** SUP  
**História:**  
Como supervisor, quero visualizar dashboards com indicadores de atendimento, para acompanhar o desempenho da equipe.  
**Critérios de Aceitação:**  
- Deve exibir chamados por status, tempo médio, SLA, etc.  
- Deve permitir filtros por período, técnico e cliente  
**Prioridade:** Alta  
**Dificuldade:** Alta  
**Dependência:** US006  

---

#### ID: US014  
**Título:** Gerenciar base de conhecimento  
**Persona:** SUP, ATD  
**História:**  
Como atendente ou supervisor, quero criar e manter artigos na base de conhecimento, para auxiliar nos atendimentos.  
**Critérios de Aceitação:**  
- Deve permitir criar, editar, publicar e desativar artigos  
- Deve permitir avaliação dos artigos pelos leitores  
- Artigos devem ter categorias e palavras-chave  
**Prioridade:** Alta  
**Dificuldade:** Alta  
**Dependência:** US004  

---

#### ID: US015  
**Título:** Gerenciamento de contratos de serviço  
**Persona:** ADM  
**História:**  
Como administrador, quero cadastrar e controlar contratos de serviço por cliente, para que o sistema saiba quais tipos de chamados e SLAs estão cobertos.  
**Critérios de Aceitação:**  
- Permitir associar contratos a produtos e clientes  
- Definir tipos de chamados permitidos e SLAs vinculados  
- Impedir abertura de chamados fora do escopo (ou alertar)  
**Prioridade:** Alta  
**Dificuldade:** Alta  
**Dependência:** US007, US008  

---

#### ID: US016  
**Título:** Visualização de SLA dos chamados  
**Persona:** CLI, SUP  
**História:**  
Como cliente ou supervisor, quero visualizar o SLA definido para cada chamado, para acompanhar se o atendimento está dentro do prazo acordado.  
**Critérios de Aceitação:**  
- Mostrar tipo de SLA (Padrão, Crítico etc.) no detalhe do chamado  
- Mostrar tempo restante e violado (se aplicável)  
- Destaque visual para status que ultrapassaram o SLA  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** US003  

---

#### ID: US017  
**Título:** Geração e download de relatórios gerenciais  
**Persona:** SUP, ADM  
**História:**  
Como supervisor ou administrador, quero gerar e baixar relatórios gerenciais em PDF ou Excel, para analisar o desempenho dos atendimentos e tomar decisões estratégicas.  
**Critérios de Aceitação:**  
- Deve permitir seleção de período, tipo de chamado, cliente e técnico  
- Deve oferecer opção de download em PDF e Excel  
- Relatórios devem refletir os mesmos dados visualizados nos dashboards  
- Apenas usuários com perfil SUP ou ADM podem acessar essa função  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** US013, RT006  

---

## 4. Requisitos Técnicos (Requisitos Não-Funcionais)

### 4.1 Overview dos Requisitos Técnicos (Ordenados por Execução)

| ID     | Descrição                                             | Prioridade | Dependência | Dificuldade |
|--------|--------------------------------------------------------|------------|-------------|-------------|
| RT001  | Utilizar autenticação por email/senha com 2FA         | Alta       | -           | Alta        |
| RT005  | Compatibilidade com navegadores modernos               | Alta       | -           | Baixa       |
| RT004  | API REST para integração com sistemas externos         | Alta       | RT001       | Alta        |
| RT003  | Logs de auditoria de ações críticas                    | Alta       | RT001       | Média       |
| RT006  | Exportação de relatórios em PDF e Excel                | Alta       | US006       | Média       |
| RT002  | Backup diário com retenção de 30 dias                  | Média      | -           | Baixa       |

---

### 4.2 Requisitos Técnicos Detalhados (Ordenados por ID)

#### ID: RT001  
**Título:** Autenticação com 2FA  
**Descrição:**  
Implementar autenticação por email e senha com verificação em dois fatores (2FA) para garantir segurança no acesso ao sistema.  
**Prioridade:** Alta  
**Dificuldade:** Alta  
**Dependência:** -  

---

#### ID: RT002  
**Título:** Backup automático  
**Descrição:**  
Executar rotinas de backup diariamente com retenção mínima de 30 dias para prevenção de perdas.  
**Prioridade:** Média  
**Dificuldade:** Baixa  
**Dependência:** -  

---

#### ID: RT003  
**Título:** Logs de auditoria de ações críticas  
**Descrição:**  
Registrar atividades relevantes no sistema para rastreabilidade e segurança, como logins, alterações e exclusões.  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** RT001  

---

#### ID: RT004  
**Título:** Integração via API REST  
**Descrição:**  
Disponibilizar e consumir APIs RESTful para integração com sistemas externos (ex: ERP, CRM).  
**Prioridade:** Alta  
**Dificuldade:** Alta  
**Dependência:** RT001  

---

#### ID: RT005  
**Título:** Compatibilidade com navegadores modernos  
**Descrição:**  
O sistema deve funcionar de forma consistente nos principais navegadores (Chrome, Firefox, Edge e Safari).  
**Prioridade:** Alta  
**Dificuldade:** Baixa  
**Dependência:** -  

---

#### ID: RT006  
**Título:** Exportação de relatórios em PDF e Excel  
**Descrição:**  
Gerar relatórios customizáveis e exportá-los em PDF e/ou Excel para análise externa.  
**Prioridade:** Alta  
**Dificuldade:** Média  
**Dependência:** US006  

---

## 5. Backlog do Produto (Ordenado por Execução)

| ID    | Título                                      | Tipo      | Prioridade | Dependência  | Dificuldade |
| ----- | ------------------------------------------- | --------- | ---------- | ------------ | ----------- |
| RT001 | Autenticação com 2FA                        | Técnico   | Alta       | -            | Alta        |
| RT005 | Compatibilidade com navegadores modernos    | Técnico   | Alta       | -            | Baixa       |
| US001 | Abertura de chamado técnico                 | Funcional | Alta       | RT001        | Média       |
| US003 | Consulta de status do chamado               | Funcional | Alta       | US001        | Baixa       |
| US002 | Atribuição automática de chamado            | Funcional | Alta       | US001        | Alta        |
| US004 | Sugestão automática da base de conhecimento | Funcional | Alta       | US001, RT004 | Alta        |
| US005 | Registro de autoatendimento como chamado    | Funcional | Média      | US004        | Média       |
| US006 | Controle de tempo por atendimento           | Funcional | Alta       | US002        | Alta        |
| RT004 | Integração via API REST                     | Técnico   | Alta       | RT001        | Alta        |
| RT003 | Logs de auditoria de ações críticas         | Técnico   | Alta       | RT001        | Média       |
| RT006 | Exportação de relatórios em PDF e Excel     | Técnico   | Alta       | US006        | Média       |
| US007 | Cadastro de produtos e serviços             | Funcional | Alta       | -            | Média       |
| US008 | Cadastro de pessoas físicas e jurídicas     | Funcional | Alta       | -            | Média       |
| US009 | Cadastro de usuários do sistema             | Funcional | Alta       | RT001        | Média       |
| US010 | Visualizar produtos e serviços vinculados   | Funcional | Média      | US007, US008 | Baixa       |
| US011 | Notificações por e-mail                     | Funcional | Alta       | US001        | Média       |
| US012 | Avaliação de atendimento                    | Funcional | Alta       | US003        | Média       |
| US013 | Visualização de dashboards                  | Funcional | Alta       | US006        | Alta        |
| US014 | Gerenciar base de conhecimento              | Funcional | Alta       | US004        | Alta        |
| US015 | Gerenciamento de contratos de serviço       | Funcional | Alta       | US007, US008 | Alta        |
| US016 | Visualização de SLA dos chamados            | Funcional | Alta       | US003        | Média       |
| US017 | Geração e download de relatórios gerenciais | Funcional | Alta       | US013, RT006 | Média       |
| RT002 | Backup automático                           | Técnico   | Média      | -            | Baixa       |

---

## 6. Critérios Gerais de Aceitação

- Todas as histórias devem ter critérios de aceitação objetivos e testáveis.  
- As funcionalidades devem ser pequenas o suficiente para serem desenvolvidas em 1 sprint.  
- Deve haver ao menos 80% de cobertura de testes automatizados.  
- O sistema deve passar por validação em ambiente de homologação com a BRISA.  
- Documentação técnica e manual do usuário devem ser entregues junto com o produto final.
