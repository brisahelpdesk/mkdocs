# Justificativa de Uso da Arquitetura de Sistema

## Versões

| Data       | Versão | Descrição                  | Responsáveis               |
|------------|--------|----------------------------|----------------------------|
| 08/06/2025 | 1.0    | Criação do documento       | [Maelton Lima dos Santos](https://github.com/Maelton)    |

## Descrição

A arquitetura foi escolhida para equilibrar manutenção, escalabilidade e simplicidade, ideal para uma equipe acadêmica e uma aplicação de porte médio.

O sistema BRISA Helpdesk será acessado por interface web responsiva e incluirá fluxos iniciais de segurança como primeiro acesso com pergunta de segurança, login com 2FA e perfis de acesso diferenciados.

Essa arquitetura foi adotada por ser:
- Mais simples de desenvolver, manter e testar
- Adequada para equipes pequenas ou acadêmicas
- Eficiente para MVPs e sistemas de porte médio
- Mais fácil de hospedar em ambientes gratuitos

A extração futura de módulos como `ReportModule` ou `KnowledgeBaseModule` como microserviços é viável, caso haja necessidade de escalabilidade específica.

A escolha das tecnologias visa atender aos requisitos de desempenho, rastreabilidade, integração via API e responsividade, conforme esperado pela BRISA.

---

## Considerações Finais

Essa arquitetura atende aos requisitos funcionais e não funcionais identificados, incluindo:
- Abertura e atribuição de chamados
- Controle de tempo e aplicação de SLA
- Autoatendimento com base de conhecimento integrada
- Notificações, relatórios e dashboards
- Controle de acesso baseado em contratos e perfis

Ela permite evolução incremental, escalabilidade progressiva e facilidade de manutenção com separação clara de responsabilidades.
