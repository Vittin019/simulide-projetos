# Contador BCD de dois dígitos

Contador decimal que usa um botão como clock e mostra dois dígitos nos displays de 7 segmentos.

## Como funciona
- Dois contadores BCD **CD4510** (crescente/decrescente, pino U/!D em comum).
- O **Cout** do primeiro é ligado ao **Clk** do segundo: quando o primeiro dígito passa de 9, o segundo avança.
- Dois decodificadores **74HC4511** convertem o BCD para 7 segmentos.
- Um botão (*Push*) faz o papel de clock.

## Arquivo
`contador_bcd.sim1` (salvo no SimulIDE 1.1.0-SR1)

---
Feito por mim (Vittin019)
