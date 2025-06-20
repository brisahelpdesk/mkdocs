# Processo de Criação de Cliente

## Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 20/06/2025 | 1.0    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton) |

## Descrição

Processo de criação de novos clientes no sistema.

## Diagrama de Sequência

``` mermaid
sequenceDiagram
    participant ADMIN
    participant SYSTEM
    participant DATABASE
    participant CLIENT

    ADMIN->>SYSTEM: Create new client request
    SYSTEM->>DATABASE: Check if user identifier exists
    DATABASE-->>SYSTEM: User exists / User does not exist

    alt User already exists
        SYSTEM-->>ADMIN: Return error (User already exists)
    else User does not exist
        SYSTEM->>DATABASE: Create new user
        SYSTEM->>CLIENT: Send first access link via email
        SYSTEM-->>ADMIN: Return success
    end
```

## Descrição do Processo

#### 1. Inicialização do processo  
   O administrador de sistema envia uma requisição ao sistema para criar um novo cliente.

#### 2. Verificação de pré-existencia de cliente  
   O sistema consulta o banco de dados para verificar se já existe um cliente com o mesmo identificador.

#### 3. Resposta de verificação  
   O banco de dados responde informando se o cliente já existe ou não.

#### 4. Caso o cliente já exista  
   O sistema retorna uma mensagem de erro para o administrador do sitema, informando que o usuário já está cadastrado.

#### 5. Caso o cliente não exista   

##### 5.1. Inserção de usuário no banco
   O sistema cria um novo registro de cliente no banco de dados.
   
##### 5.2. Disparo de email de primeiro acesso 
   O sistema envia ao cliente um link de primeiro acesso ao sistema, por e-mail.
    
##### 5.3. Resposta de sucesso
   O sistema retorna uma resposta de sucesso ao administrador de sistema, confirmando a criação do novo usuário.
