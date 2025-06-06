# Catálogo de Requisitos Ágeis – Projeto BRISA Helpdesk  

## 1. Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 06/05/2025 | 0.1    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton)    |

---

## 2. Personas

| ID   | Persona      | Descrição                                                                 |
|------|--------------|--------------------------------------------------------------------------|
| ADM  | Administrador | Gerencia configurações, usuários, artigos e parâmetros do sistema.        |
| SUP  | Supervisor    | Acompanha chamados da equipe, reatribui e aprova artigos da base de conhecimento. |
| ATD  | Atendente     | Recebe e resolve chamados; pode sugerir conteúdos para a base.             |
| CLI  | Solicitante   | Cliente que abre chamados e consulta seu status.                          |
| VIS  | Visitante     | Usuário sem login que pode consultar a base pública de conhecimento (se permitido). |

---

## 3. Requisitos (Histórias de Usuário)

### ID: US001  
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

---

### ID: US002  
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

---

### ID: US003  
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

---

### ID: US004  
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

---

### ID: US006  
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

---

### ID: US005  
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

---

## 4. Requisitos Técnicos

| ID     | Descrição                                             | Prioridade | Dependência | Dificuldade |
|--------|--------------------------------------------------------|------------|-------------|-------------|
| RT001  | Utilizar autenticação por email/senha com 2FA         | Alta       | -           | Alta        |
| RT005  | Compatibilidade com navegadores modernos               | Alta       | -           | Baixa       |
| RT004  | API REST para integração com sistemas externos         | Alta       | RT001       | Alta        |
| RT003  | Logs de auditoria de ações críticas                    | Alta       | RT001       | Média       |
| RT006  | Exportação de relatórios em PDF e Excel                | Alta       | US006       | Média       |
| RT002  | Backup diário com retenção de 30 dias                  | Média      | -           | Baixa       |

---

## 5. Backlog do Produto

| ID     | Título                                         | Tipo       | Prioridade | Dependência   | Dificuldade |
|--------|------------------------------------------------|------------|------------|----------------|-------------|
| RT001  | Autenticação com 2FA                           | Técnico    | Alta       | -              | Alta        |
| RT005  | Compatibilidade com navegadores modernos       | Técnico    | Alta       | -              | Baixa       |
| US001  | Abertura de chamado técnico                    | Funcional  | Alta       | RT001          | Média       |
| US003  | Consulta de status do chamado                  | Funcional  | Alta       | US001          | Baixa       |
| US002  | Atribuição automática de chamado               | Funcional  | Alta       | US001          | Alta        |
| US004  | Sugestão automática da base de conhecimento    | Funcional  | Alta       | US001, RT004   | Alta        |
| RT004  | Integração via API REST                        | Técnico    | Alta       | RT001          | Alta        |
| RT003  | Logs de auditoria de ações críticas            | Técnico    | Alta       | RT001          | Média       |
| US006  | Controle de tempo por atendimento              | Funcional  | Alta       | US002          | Alta        |
| RT006  | Exportação de relatórios em PDF e Excel        | Técnico    | Alta       | US006          | Média       |
| US005  | Registro de autoatendimento como chamado       | Funcional  | Média      | US004          | Média       |
| RT002  | Backup automático                              | Técnico    | Média      | -              | Baixa       |

---

## 6. Critérios Gerais de Aceitação

- Todas as histórias devem ter critérios de aceitação objetivos e testáveis.  
- As funcionalidades devem ser pequenas o suficiente para serem desenvolvidas em 1 sprint.  
- Deve haver ao menos 80% de cobertura de testes automatizados.  
- O sistema deve passar por validação em ambiente de homologação com a BRISA.  
- Documentação técnica e manual do usuário devem ser entregues junto com o produto final.  
