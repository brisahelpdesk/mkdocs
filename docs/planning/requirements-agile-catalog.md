# Catálogo de Requisitos Ágeis – Projeto BRISA Helpdesk  

## 1. Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 06/05/2025 | 0.1    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton)    |
| 06/05/2025 | 0.2    | Descreve requisitos        | [Maelton Lima dos Santos](https://github.com/Maelton)    |

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

## 3. Histórias de Usuário (Requisitos Funcionais)

### 3.1 Overview das Histórias de Usuário (Ordenadas por Execução)

| ID     | Título                                        | Descrição                                                                                      | Dependência       |
|--------|-----------------------------------------------|------------------------------------------------------------------------------------------------|-------------------|
| US001  | Abertura de chamado técnico                   | Permitir que o solicitante crie chamados com anexos e tipo definido.                          | RT001             |
| US003  | Consulta de status do chamado                 | Exibir o andamento, histórico e anexos de um chamado.                                         | US001             |
| US002  | Atribuição automática de chamado              | Distribuir chamados automaticamente para técnicos com menor carga.                            | US001             |
| US004  | Sugestão automática da base de conhecimento   | Sugerir artigos da base ao abrir chamado conforme palavras-chave.                             | US001, RT004      |
| US006  | Controle de tempo por atendimento             | Permitir que o técnico registre o tempo gasto em cada atendimento.                            | US002             |
| US005  | Registro de autoatendimento como chamado      | Gerar automaticamente um chamado ao consultar artigo da base de conhecimento.                 | US004             |

---

### 3.2 Histórias de Usuário Detalhadas (Ordenados por ID)

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
