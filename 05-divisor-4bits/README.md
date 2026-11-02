# Divisor de 4 bits

Circuito digital que realiza a divisão de um número de 4 bits (dividendo **N**) por outro de 4 bits (divisor **D**).

O resultado é mostrado em displays de 7 segmentos:
- **Parte inteira** do quociente
- **Uma casa decimal** (fração)

Há também um LED de erro que acende em caso de **divisão por zero** (D = 0).

## Como funciona (visão geral)

O circuito usa o algoritmo de divisão restauradora (restoring division) com registradores de deslocamento e somadores/subtratores, adaptado para também calcular a parte fracionária (multiplicando o resto por 10 e dividindo de novo).

### Principais blocos
- **DREG (74HC194)**: guarda o divisor
- **NQ (74HC194)**: acumula o quociente inteiro
- **R (74HC194)**: guarda o resto parcial
- **XQ (74HC194)**: casa decimal
- **283-SUB**: subtração (resto − divisor)
- **283-X10**: multiplica o resto por 10 (8R + 2R) para a casa decimal
- **Contador 74HC161**: controla a sequência de passos
- **Mux 74HC157**: seleciona a entrada do resto
- Portas AND/OR e inversores para gerar os sinais de controle (S0/S1 dos 194, loads, etc.)
- **MC14495 + 7-segmentos**: decodificação e visualização de N, D, quociente e decimal
- LED de erro para detecção de zero no divisor

## Arquivo
`divisor_4bits.sim1` (SimulIDE 1.1.0-SR2)

Clock de 1 kHz.

---
Feito por mim (Vittin019)
