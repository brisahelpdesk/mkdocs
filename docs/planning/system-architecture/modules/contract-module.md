# ContractModule (Módulo de Contratos de Serviço)

O `ContractModule` é responsável pelo gerenciamento dos contratos de suporte firmados entre a empresa e seus clientes. Ele define quais produtos e serviços estão cobertos, quais tipos de chamados são permitidos por cliente, e quais regras de SLA devem ser aplicadas em cada caso.

---

## Objetivo Principal

Restringir ou permitir a abertura de chamados com base em regras contratuais, garantindo que o atendimento esteja alinhado com os acordos firmados com cada cliente.

---

## O que o ContractModule faz

| Função                                     | Descrição                                                                 |
|-------------------------------------------|---------------------------------------------------------------------------|
| Cadastro de contratos por cliente         | Permite vincular contratos a pessoas físicas ou jurídicas                 |
| Associação de produtos e serviços         | Define quais itens estão cobertos por cada contrato                       |
| Restrição de tipos de chamado             | Limita quais categorias de chamados podem ser abertos por contrato        |
| Definição de SLA vinculado                | Estabelece prazos específicos de atendimento conforme o contrato          |
| Validação na abertura de chamado          | Impede ou alerta sobre chamados fora do escopo contratual                 |
| Controle de vigência e status             | Permite ativar, desativar ou encerrar contratos conforme o período válido |
