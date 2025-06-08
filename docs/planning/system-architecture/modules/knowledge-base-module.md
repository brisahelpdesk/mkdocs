# KnowledgeBaseModule (Módulo da Base de Conhecimento)

O `KnowledgeBaseModule` é responsável por gerenciar os artigos da base de conhecimento utilizados tanto no autoatendimento quanto durante os atendimentos técnicos. Ele permite a criação, edição, categorização e publicação de conteúdos que auxiliam os usuários na resolução de dúvidas e problemas de forma autônoma.

---

## Objetivo Principal

Oferecer um repositório estruturado de artigos e tutoriais que possam ser sugeridos automaticamente aos usuários, promovendo a resolução rápida de chamados e reduzindo a carga de atendimento humano.

---

## O que o KnowledgeBaseModule faz

| Função                                   | Descrição                                                                  |
|-----------------------------------------|----------------------------------------------------------------------------|
| Criação e edição de artigos             | Permite que técnicos ou supervisores escrevam e atualizem conteúdos        |
| Classificação por categorias e palavras-chave | Cada artigo pode ser vinculado a temas e tags relevantes                |
| Controle de publicação                  | Artigos passam por revisão antes de serem publicados                      |
| Desativação sem exclusão                | Artigos podem ser desativados sem perda do histórico                      |
| Avaliação pelos leitores                | Usuários podem avaliar se o conteúdo foi útil ou não                      |
| Sugestão automática ao abrir chamado    | Base para a recomendação automática de artigos no módulo de autoatendimento |
| Uso como referência em atendimentos     | Técnicos podem vincular artigos a interações em chamados                  |

---

## Relacionamento com Banco de Dados e Object Storage

### Relacionamento com o Banco de Dados (PostgreSQL)

O banco de dados armazena todas as **informações estruturadas dos artigos**, como:

| Campo                              | Função                                                           |
|-----------------------------------|------------------------------------------------------------------|
| `id`, `titulo`, `conteudo`        | Identificação e corpo do artigo                                 |
| `palavras_chave`, `categoria_id`  | Indexação e classificação                                       |
| `autor_id`, `status`              | Controle de autoria e fluxo de aprovação/publicação             |
| `avaliacoes`                      | Notas e feedbacks dados pelos leitores                          |
| `data_publicacao`, `ativo`        | Controle de visibilidade e histórico                            |

Ou seja, **todo o conteúdo textual e metadados** são persistidos no banco de dados.

---

### Relacionamento com o Object Storage (S3/Firebase)

O object storage é utilizado quando o artigo possui **anexos** (como imagens, PDFs, vídeos etc.), e armazena:

- Imagens explicativas (ex: prints de tela)
- Documentos vinculados (manuais, formulários)
- Vídeos tutoriais ou gravações

Nesse caso:

- O arquivo é enviado para o S3/Firebase via SDK
- A **URL do arquivo** é armazenada em uma tabela no banco, como `artigo_anexos`, com referência ao campo `artigo_id`
