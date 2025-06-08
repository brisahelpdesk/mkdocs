# SelfServiceModule (Módulo de Autoatendimento)

O `SelfServiceModule` é responsável por registrar interações de autoatendimento dos usuários na base de conhecimento, transformando essas ações em chamados automáticos quando necessário. Ele visa oferecer suporte imediato sem intervenção humana, ao mesmo tempo em que mantém controle estatístico das tentativas de resolução autônoma.

---

## Objetivo Principal

Oferecer ao usuário uma primeira camada de suporte automatizado e registrar essas interações como chamados do tipo “Autoatendimento”, facilitando o monitoramento e a tomada de decisão sobre melhorias na base de conhecimento.

---

## O que o SelfServiceModule faz

| Função                                    | Descrição                                                                 |
|------------------------------------------|---------------------------------------------------------------------------|
| Sugere artigos automaticamente            | Com base nas palavras-chave digitadas ao abrir um chamado                 |
| Registra interações com artigos          | Cada clique em um artigo é logado como tentativa de autoatendimento       |
| Gera chamado automático                   | Cria um chamado do tipo “Autoatendimento” com status “Em Consulta”        |
| Finaliza ou converte o chamado            | Se o artigo resolver o problema, o chamado é marcado como “Resolvido”; caso contrário, o usuário pode convertê-lo em um chamado técnico |
| Permite avaliação do artigo               | O usuário pode indicar se o artigo ajudou ou não                          |
| Alimenta relatórios e dashboards          | Dados de autoatendimento são considerados em métricas de desempenho       |
