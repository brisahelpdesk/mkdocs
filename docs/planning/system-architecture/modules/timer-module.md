# TimerModule (Módulo de Controle de Tempo)

O `TimerModule` é responsável por registrar o tempo gasto pelos técnicos em cada atendimento. Ele permite iniciar, pausar, retomar e finalizar a contagem de tempo durante interações em chamados, garantindo a medição precisa do esforço despendido.

---

## Objetivo Principal

Registrar com precisão o tempo de atendimento técnico para fins de acompanhamento de produtividade, cumprimento de SLA, geração de relatórios e visibilidade gerencial.

---

## O que o TimerModule faz

| Função                            | Descrição                                                                   |
|-----------------------------------|-----------------------------------------------------------------------------|
| Iniciar temporizador              | Inicia a contagem de tempo ao começar uma interação                         |
| Pausar temporizador               | Permite suspender temporariamente a contagem                                |
| Retomar temporizador              | Retoma o cronômetro pausado anteriormente                                   |
| Finalizar temporizador            | Encerra o tempo registrado em uma interação ou atendimento                  |
| Exibir tempo por interação        | Mostra a duração individual de cada bloco de atendimento                    |
| Calcular tempo total por chamado  | Soma o tempo total gasto em todas as interações daquele chamado             |
| Exportar dados                    | Os tempos são utilizados em relatórios e dashboards                         |
