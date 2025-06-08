# AssignmentModule (Módulo de Atribuição Automática)

O `AssignmentModule` é responsável por distribuir automaticamente os chamados entre os técnicos disponíveis, com base em regras de carga de trabalho, disponibilidade e perfil de atuação. O objetivo é balancear o volume de atendimentos e reduzir o tempo de resposta sem depender de intervenção manual.

---

## Objetivo Principal

Atribuir chamados abertos aos técnicos mais adequados com base em critérios objetivos, promovendo eficiência, equilíbrio de carga e agilidade no atendimento.

---

## O que o AssignmentModule faz

| Função                                 | Descrição                                                                 |
|---------------------------------------|---------------------------------------------------------------------------|
| Identifica técnicos elegíveis         | Considera apenas técnicos ativos e habilitados                           |
| Verifica carga de trabalho            | Avalia o número de chamados ativos por técnico                           |
| Resolve empates aleatoriamente        | Em caso de empate entre técnicos com mesma carga, escolhe aleatoriamente |
| Atribui técnico ao chamado            | Define e registra automaticamente o responsável pelo chamado             |
| Permite reatribuição manual posterior | Supervisores ainda podem modificar a atribuição após o processo automático |
| Considera perfil ou especialidade     | (opcional) Pode ser configurado para levar em conta área de atuação      |
