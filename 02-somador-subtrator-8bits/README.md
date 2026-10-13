# Somador/subtrator de 8 bits

Variação do somador de 8 bits que também subtrai, com lógica de overflow e de sinal negativo.

## Como funciona
- Dois 74HC283 em cascata (Co → Ci).
- Dois 74HC86 (XOR) complementam o bloco B quando a operação é subtração. O mesmo sinal vai para o Ci, o que dá o complemento de 2.
- Portas AND, OR e buffers formam os blocos **Lógica Overflow (+1)** e **Lógica Sinal Negativo** indicados no esquema.
- Um 74HC08 e um CD4511 completam a parte de sinal. Seis MC14495 mostram os valores em hexadecimal.

## Arquivo
`somador_subtrator_8bits.sim1` (salvo no SimulIDE 1.1.0-SR1)

---
Feito por mim (Vittin019)
