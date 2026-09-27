# Lab 02 — Escalonamento de CPU

## Objetivo
Simular e comparar os algoritmos **FCFS**, **Round Robin** e **SJF não-preemptivo**.

## Processos

| Processo | Chegada | Duração |
|---|---:|---:|
| P1 | 0 ms | 8 ms |
| P2 | 1 ms | 4 ms |
| P3 | 2 ms | 9 ms |
| P4 | 3 ms | 5 ms |

## 1. Efeito Comboio — FCFS

Ordem:

```text
P1 → P2 → P3 → P4
```

O P2, mesmo sendo curto, precisou esperar o P1 terminar. Isso demonstra o **efeito comboio**.

**Resultados:**
- Espera média: **8,75 ms**
- Retorno médio: **15,25 ms**

![FCFS](evidencias/fcfs_rr3.png)

## 2. Variação do Quantum — Round Robin

| Quantum | Espera Média | Retorno Médio |
|---|---:|---:|
| 1 ms | 12,50 ms | 19,00 ms |
| 3 ms | 13,50 ms | 20,00 ms |
| 50 ms | 8,75 ms | 15,25 ms |

Com **1 ms**, há mais trocas de contexto.  
Com **50 ms**, cada processo termina em uma única vez e o comportamento se aproxima do FCFS.

![Round Robin](evidencias/quantum_1_50.png)

## 3. SJF Não-Preemptivo

Ordem:

```text
P1 → P2 → P4 → P3
```

| Processo | Espera | Retorno |
|---|---:|---:|
| P1 | 0 ms | 8 ms |
| P2 | 7 ms | 11 ms |
| P4 | 9 ms | 14 ms |
| P3 | 15 ms | 24 ms |

**Médias:**
- Espera: **7,75 ms**
- Retorno: **14,25 ms**

## Comparação Final

| Algoritmo | Espera Média | Retorno Médio |
|---|---:|---:|
| FCFS | 8,75 ms | 15,25 ms |
| Round Robin (3 ms) | 13,50 ms | 20,00 ms |
| SJF | 7,75 ms | 14,25 ms |

Para esta carga de trabalho, o **SJF apresentou os menores tempos médios**.

## Execução 

```bash
python simulador_escalonador.py
```
