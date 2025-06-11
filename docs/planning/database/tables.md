### USER
| Campo                | Tipo         | Descrição                                 | Restrições               |
|----------------------|--------------|-------------------------------------------|--------------------------|
| user_id              | UUID         | Identificador único                       | PK, NOT NULL             |
| name                 | VARCHAR(100) | Nome completo                             | NOT NULL                 |
| email                | VARCHAR(100) | E-mail (login)                            | UNIQUE, NOT NULL         |
| password_hash        | VARCHAR(255) | Hash da senha                             | NOT NULL                 |
| two_factor_enabled   | BOOLEAN      | 2FA ativado                               | DEFAULT FALSE            |
| is_active            | BOOLEAN      | Usuário ativo                             | DEFAULT TRUE             |
| last_login           | TIMESTAMP    | Último acesso                             |                          |
| created_at           | TIMESTAMP    | Data de criação                           | DEFAULT CURRENT_TIMESTAMP|
| updated_at           | TIMESTAMP    | Data de atualização                       |                          |

### PERMISSION
| Campo             | Tipo          | Descrição                              | Restrições               |
|-------------------|---------------|----------------------------------------|--------------------------|
| permission_id     | UUID          | Identificador único                   | PK, NOT NULL             |
| code              | VARCHAR(50)   | Código único (ex: "TICKET_CREATE")    | UNIQUE, NOT NULL         |
| name              | VARCHAR(100)  | Nome legível                          | NOT NULL                 |
| description       | TEXT          | Descrição detalhada                   |                          |
| category          | VARCHAR(50)   | Agrupamento (ex: "Tickets", "KB")     |                          |
| created_at        | TIMESTAMP     | Data de criação                       | DEFAULT CURRENT_TIMESTAMP|

### ROLE (substitui USER_ROLE)
| Campo             | Tipo          | Descrição                              | Restrições               |
|-------------------|---------------|----------------------------------------|--------------------------|
| role_id           | UUID          | Identificador único                   | PK, NOT NULL             |
| name              | VARCHAR(50)   | Nome do perfil (ex: "Administrador")  | UNIQUE, NOT NULL         |
| is_system         | BOOLEAN       | Perfil padrão do sistema              | DEFAULT FALSE            |
| created_at        | TIMESTAMP     | Data de criação                       | DEFAULT CURRENT_TIMESTAMP|

### ROLE_PERMISSION (tabela de junção)
| Campo             | Tipo          | Descrição                              | Restrições               |
|-------------------|---------------|----------------------------------------|--------------------------|
| role_permission_id| UUID          | Identificador único                   | PK, NOT NULL             |
| role_id           | UUID          | Referência ao perfil                  | FK → ROLE, NOT NULL      |
| permission_id     | UUID          | Referência à permissão                | FK → PERMISSION, NOT NULL|
| granted_at        | TIMESTAMP     | Data de concessão                     | DEFAULT CURRENT_TIMESTAMP|
| granted_by        | UUID          | Quem concedeu                         | FK → USER                |

### USER_ROLE (agora tabela de junção)
| Campo             | Tipo          | Descrição                              | Restrições               |
|-------------------|---------------|----------------------------------------|--------------------------|
| user_role_id      | UUID          | Identificador único                   | PK, NOT NULL             |
| user_id           | UUID          | Referência ao usuário                 | FK → USER, NOT NULL      |
| role_id           | UUID          | Referência ao perfil                  | FK → ROLE, NOT NULL      |
| assigned_by       | UUID          | Quem atribuiu                         | FK → USER                |
| assigned_at       | TIMESTAMP     | Data de atribuição                    | DEFAULT CURRENT_TIMESTAMP|
| is_active         | BOOLEAN       | Atribuição ativa                      | DEFAULT TRUE             |

### TICKET
| Campo                | Tipo         | Descrição                                  | Restrições               |
|----------------------|--------------|--------------------------------------------|--------------------------|
| ticket_id            | UUID         | Identificador único                       | PK, NOT NULL             |
| code                 | VARCHAR(20)  | Código legível (ex: BR-2025-0001)         | UNIQUE, NOT NULL         |
| title                | VARCHAR(100) | Título resumido                           | NOT NULL                 |
| description          | TEXT         | Descrição detalhada                       | NOT NULL                 |
| requester_id         | UUID         | Usuário solicitante                       | FK → USER, NOT NULL      |
| current_status       | VARCHAR(50)  | Status atual                              | FK → TICKET_STATUS       |
| ticket_type_id       | UUID         | Tipo de chamado                           | FK → TICKET_TYPE, NOT NULL|
| priority_id          | UUID         | Prioridade                                | FK → TICKET_PRIORITY     |
| product_id           | UUID         | Produto relacionado                       | FK → PRODUCT             |
| sla_id               | UUID         | SLA aplicável                             | FK → SLA                 |
| contract_id          | UUID         | Contrato vinculado                        | FK → CONTRACT            |
| created_at           | TIMESTAMP    | Data de abertura                          | DEFAULT CURRENT_TIMESTAMP|
| updated_at           | TIMESTAMP    | Última atualização                        |                          |
| closed_at            | TIMESTAMP    | Data de encerramento                      |                          |
| closed_by            | UUID         | Quem encerrou                             | FK → USER                |
| reopened_count       | INTEGER      | Número de reaberturas                     | DEFAULT 0                |

### TICKET_STATUS
| Campo                | Tipo         | Descrição                                  | Restrições               |
|----------------------|--------------|--------------------------------------------|--------------------------|
| status_id            | UUID         | Identificador único                       | PK, NOT NULL             |
| name                 | VARCHAR(50)  | Nome do status                            | NOT NULL                 |
| description          | VARCHAR(255) | Descrição                                 |                          |
| is_active            | BOOLEAN      | Status ativo no sistema                   | DEFAULT TRUE             |
| allows_reopen        | BOOLEAN      | Permite reabertura deste status           | DEFAULT FALSE            |

### TICKET_TYPE
| Campo                | Tipo         | Descrição                                  | Restrições               |
|----------------------|--------------|--------------------------------------------|--------------------------|
| type_id              | UUID         | Identificador único                       | PK, NOT NULL             |
| name                 | VARCHAR(50)  | Nome do tipo                              | NOT NULL                 |
| description          | VARCHAR(255) | Descrição                                 |                          |
| is_active            | BOOLEAN      | Tipo ativo no sistema                     | DEFAULT TRUE             |

### TICKET_PRIORITY
| Campo                | Tipo         | Descrição                                  | Restrições               |
|----------------------|--------------|--------------------------------------------|--------------------------|
| priority_id          | UUID         | Identificador único                       | PK, NOT NULL             |
| name                 | VARCHAR(50)  | Nome da prioridade                        | NOT NULL                 |
| level                | INTEGER      | Nível (1-5)                               | NOT NULL, UNIQUE         |
| color                | VARCHAR(20)  | Cor para exibição                         |                          |
| is_default           | BOOLEAN      | Prioridade padrão para novos chamados     | DEFAULT FALSE            |

### TICKET_ASSIGNMENT
| Campo                | Tipo         | Descrição                                  | Restrições               |
|----------------------|--------------|--------------------------------------------|--------------------------|
| assignment_id        | UUID         | Identificador único                       | PK, NOT NULL             |
| ticket_id            | UUID         | Chamado relacionado                       | FK → TICKET, NOT NULL    |
| assigned_to          | UUID         | Técnico atribuído                         | FK → USER, NOT NULL      |
| assigned_by          | UUID         | Quem fez a atribuição                     | FK → USER                |
| assignment_type      | ENUM         | AUTO/MANUAL/REASSIGNMENT                  | NOT NULL                 |
| assigned_at          | TIMESTAMP    | Data de atribuição                        | DEFAULT CURRENT_TIMESTAMP|
| unassigned_at        | TIMESTAMP    | Data de desatribuição                     |                          |
| is_current           | BOOLEAN      | Atribuição atual                          | DEFAULT TRUE             |

### TICKET_INTERACTION
| Campo                | Tipo         | Descrição                                  | Restrições               |
|----------------------|--------------|--------------------------------------------|--------------------------|
| interaction_id       | UUID         | Identificador único                       | PK, NOT NULL             |
| ticket_id            | UUID         | Chamado relacionado                       | FK → TICKET, NOT NULL    |
| user_id              | UUID         | Autor da interação                        | FK → USER, NOT NULL      |
| interaction_type     | ENUM         | COMMENT/STATUS_CHANGE/ATTACHMENT/etc.     | NOT NULL                 |
| content              | TEXT         | Conteúdo da interação                     |                          |
| is_internal          | BOOLEAN      | Visível apenas para equipe                | DEFAULT FALSE            |
| created_at           | TIMESTAMP    | Data de criação                           | DEFAULT CURRENT_TIMESTAMP|

### TICKET_TIMER
| Campo                | Tipo         | Descrição                                  | Restrições               |
|----------------------|--------------|--------------------------------------------|--------------------------|
| timer_id             | UUID         | Identificador único                       | PK, NOT NULL             |
| ticket_id            | UUID         | Chamado relacionado                       | FK → TICKET, NOT NULL    |
| user_id              | UUID         | Técnico responsável                       | FK → USER, NOT NULL      |
| start_time           | TIMESTAMP    | Início do tempo                           | NOT NULL                 |
| end_time             | TIMESTAMP    | Fim do tempo                              |                          |
| duration             | INTEGER      | Duração em segundos                       |                          |
| is_billable          | BOOLEAN      | Tempo faturavel                           | DEFAULT TRUE             |
| notes                | TEXT         | Observações                               |                          |

### TICKET_ATTACHMENT
| Campo                | Tipo         | Descrição                                  | Restrições               |
|----------------------|--------------|--------------------------------------------|--------------------------|
| attachment_id        | UUID         | Identificador único                       | PK, NOT NULL             |
| ticket_id            | UUID         | Chamado relacionado                       | FK → TICKET, NOT NULL    |
| user_id              | UUID         | Quem anexou                               | FK → USER, NOT NULL      |
| file_name            | VARCHAR(255) | Nome original do arquivo                  | NOT NULL                 |
| file_size            | INTEGER      | Tamanho em bytes                          | NOT NULL                 |
| file_type            | VARCHAR(50)  | Tipo MIME                                 |                          |
| storage_path         | VARCHAR(255) | Caminho no armazenamento                  | NOT NULL                 |
| uploaded_at          | TIMESTAMP    | Data de upload                            | DEFAULT CURRENT_TIMESTAMP|

### TICKET_HISTORY
| Campo                | Tipo         | Descrição                                  | Restrições               |
|----------------------|--------------|--------------------------------------------|--------------------------|
| history_id           | UUID         | Identificador único                       | PK, NOT NULL             |
| ticket_id            | UUID         | Chamado relacionado                       | FK → TICKET, NOT NULL    |
| changed_by           | UUID         | Usuário que fez a alteração               | FK → USER, NOT NULL      |
| change_type          | VARCHAR(50)  | Tipo de alteração                         | NOT NULL                 |
| old_value            | TEXT         | Valor anterior                            |                          |
| new_value            | TEXT         | Novo valor                                |                          |
| changed_at           | TIMESTAMP    | Data da alteração                         | DEFAULT CURRENT_TIMESTAMP|