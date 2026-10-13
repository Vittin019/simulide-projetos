# Somador de 8 bits

Soma dois números de 8 bits (A e B) escolhidos por chaves e mostra o resultado em hexadecimal.

## Como funciona
- Dois somadores 74HC283 de 4 bits em cascata: o **Co** do primeiro entra no **Ci** do segundo.
- 16 chaves de entrada (A0–A7 e B0–B7).
- Sete decodificadores MC14495 com displays de 7 segmentos: os nibbles de A, os de B, os de A+B e o carry (overflow) final.

## Arquivo
`somador_8bits.sim1` (salvo no SimulIDE 1.0.0-SR1)

---
Feito por mim (Vittin019)
