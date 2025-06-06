# Dúvidas sobre o Sistema de Suporte a Chamados

## Atribuição de Chamados

**Pergunta:**

O processo de atribuir um chamado a um atendente será automático (usando critérios como atendente com menos demandas) ou manual (realizado pelo supervisor)?

**Resposta:**

O sistema utilizará **atribuição automática** como padrão, com possibilidade de **reatribuição manual** feita pelo supervisor.

### Como funciona a atribuição automática:

- O sistema busca o **técnico com menor carga de trabalho** na categoria específica do chamado.
- Considera **apenas técnicos ativos** e **habilitados para a categoria**.
- Em caso de empate na carga de trabalho, o sistema utiliza **seleção aleatória**.
- A atribuição acontece **imediatamente após a abertura do chamado**.

### Reatribuição manual:

Supervisores e administradores podem reatribuir chamados **a qualquer momento** por meio da interface do sistema.

---

# Dúvidas sobre o Autoatendimento (FAQ)

## Como será o sistema de autoatendimento?

O sistema contará com uma **Base de Conhecimento integrada** e inteligente, funcionando como um FAQ.

### Características principais:

- **Busca inteligente:** Pesquisa por palavra-chave.
- **Sugestões automáticas:** Durante a abertura do chamado, o sistema sugere artigos relevantes.
- **Categorização:** Organização por produto, categoria e subcategoria.
- **Avaliação de utilidade:** Usuários avaliam se o artigo foi útil (ex: 89%, 95%).

### Exemplo de sugestão:

Ao digitar "erro de conexão com banco de dados", o sistema sugere automaticamente:

- Artigo #145: *"Erro de conexão com banco de dados"*
- Artigo #267: *"Configuração de proxy corporativo"*

## Quem edita e adiciona conteúdos ao autoatendimento?

A gestão de conteúdo segue uma **hierarquia de permissões**:

### Permissões por perfil:

- **Administrador:** Criar, editar, aprovar e excluir artigos.
- **Supervisor/Gerente:** Criar, editar e aprovar artigos da sua área.
- **Atendente/Suporte:** Criar artigos (em status **"Rascunho"** até aprovação).
- **Solicitante/Cliente:** Apenas visualizam artigos ativos.

### Fluxo de aprovação:

1. Técnico cria artigo -> Status: *Rascunho*
2. Supervisor revisa -> Status: *Em Revisão*
3. Aprovação final -> Status: *Ativo*
4. Artigo disponível para todos os usuários

### Onde será hospedada a base de conhecimento?

Ela será **totalmente integrada** ao sistema principal.

### Vantagens da integração:

- Mesma autenticação (login único)
- Controle de acesso por perfil
- Sugestões durante abertura de chamados
- Métricas integradas com chamados
- Manutenção centralizada

## Registro de Autoatendimentos como Chamados

**Pergunta:** O sistema deve registrar autoatendimentos como chamados?

**Resposta:** **Sim.** O sistema criará chamados do tipo **"Autoatendimento"**, para garantir **rastreabilidade e controle completo**.

### Tipos de Chamados (Expandidos):

- Incidente
- Requisição de Serviço
- Dúvida
- Melhoria
- **Autoatendimento** <- *Novo tipo*

### Justificativas para registrar:

### 1. Evidência de Demanda Real

- Toda consulta representa uma necessidade do usuário.
- Permite rastrear problemas recorrentes.
- Histórico completo de todas as demandas.

### 2. Métricas Gerenciais Completas

- Volume total de atendimentos (técnico + autoatendimento).
- Eficiência do autoatendimento vs. técnico.
- ROI mensurável da base de conhecimento.
- Identificação de gaps (assuntos sem artigo).

### 3. Controle Unificado

- Uma base de dados para todos os tipos.
- Numeração sequencial única para auditoria.
- Relatórios integrados, sem sistemas paralelos.

---

## Funcionamento na prática

### Fluxo automático de autoatendimento:

```
1. Usuário acessa a base de conhecimento  
    
2. Sistema cria chamado automaticamente:
    - Tipo: **Autoatendimento**
    - Status: **Em Consulta**
    - Técnico: *Sistema - Base de Conhecimento*    
        
3. Se o usuário encontra a solução:
    - Status: **Resolvido - Autoatendimento**
    - Resolução: *Artigo consultado*
    - Tempo: *ex: 4 minutos*
         
4. Se **não** encontrar:
    - Converte para chamado técnico
    - Tipo: *Incidente, Dúvida, etc.*
    - Mantém histórico da tentativa
```

### Exemplo de chamado de autoatendimento:

> Chamado: #2025-000847 - Consulta sobre reset de senha
> 
> 
> **STATUS:** *RESOLVIDO - AUTOATENDIMENTO*
> 
> **Cliente:** ABC Tecnologia Ltda
> 
> **Usuário:** João Silva (joao@abc.com.br)
> 
> **Tipo:** Autoatendimento
> 
> **Aberto em:** 28/05/2025 14:30
> 
> **Resolvido em:** 28/05/2025 14:33
> 
> **Tempo total:** 3 minutos
> 
> **Artigo consultado:** #002 *"Reset de Senha"*
> 
> **Avaliação:** * * * * * *"Resolveu meu problema rapidamente"*
> 

---

## Benefícios nos Relatórios

### Dashboard Integrado

> INDICADORES DO DIA
> | Chamados Totais| Técnicos | Autoatendimento | Taxa de Sucesso | Economia Estimada |
> | :-: | :-:| :-: | :-: | :-: |
> |89 | 42 | 47 | 94% | R$2.350,00 |

### Análise de Eficiência

- **Atendimento Técnico:** 42 chamados (tempo médio: 2.8h)
- **Autoatendimento:** 47 chamados (tempo médio: 4 min)
- **Taxa de Autoatendimento:** 53%
- **Problemas comuns:** Reset senha (23%), Config proxy (18%)

### Vantagens

- Rastreabilidade completa
- Relatórios unificados
- Identificação de tendências
- ROI mensurável
- Gestão simplificada
- Auditoria completa

---

# Considerações Finais

Registrar autoatendimentos como chamados garante:

- **Controle total**
- **Métricas completas**
- **Evidência real de todas as demandas**
- **Gestão eficiente e estratégica do suporte**

---

# Dúvidas Técnicas

## Preferências Tecnológicas

**Pergunta:** Há preferência por linguagens, bancos de dados ou licenças?

**Resposta:**

**Não há preferências específicas.** Utilizar tecnologias **atuais e modernas** é desejável.

---

## Sistema de Autenticação e Perfis

**Pergunta:** Como será o sistema de autenticação? Alguma tecnologia específica?

**Resposta:**

O sistema terá **cadastro completo de usuários** com autenticação baseada em **credenciais próprias**.

### Fluxo de Cadastro e Autenticação

### 1. Cadastro de Usuários

- Administradores cadastram todos os usuários.
- Cada usuário recebe credenciais iniciais (email + senha temporária).
- Primeiro acesso obrigatório para:
    - Definir senha definitiva
    - Configurar pergunta e resposta de segurança

**Campos obrigatórios:**

- Nome completo
- Email (será o login)
- Perfil (Administrador, Supervisor, Atendente, Solicitante)
- Status (Ativo/Inativo)

### 2. Primeiro Acesso (Tela `PRI001`)

**Campos obrigatórios:**

- Nova senha (com validação)
- Confirmação de senha
- Pergunta de segurança (dropdown)
- Resposta de segurança (mínimo 4 caracteres)

### 3. Autenticação Regular

- Login via email + senha
- Validações de segurança conforme política definida