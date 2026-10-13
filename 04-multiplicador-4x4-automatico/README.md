# Multiplicador sequencial 4×4 automático

Multiplica dois números de 4 bits (A e B, por chaves) e mostra o produto de 8 bits em **hexadecimal** (por exemplo, 15×15 = 225 aparece como **E1**). Não precisa de botão de clock, chave de carga nem reset: o ciclo repete sozinho e o resultado se atualiza ao mexer nas chaves.

## Ideia: somar e deslocar
Para cada bit de B, do menor ao maior: se o bit for 1, soma A no nibble alto do produto; depois desloca o produto uma casa à direita. Em 4 passos o produto está pronto. Exemplo, 3×3:

| Passo | Produto (alto, baixo) |
|---|---|
| carga | 0000 0011 |
| 1 | 0001 1001 |
| 2 | 0010 0100 |
| 3 | 0001 0010 |
| 4 | 0000 1001 = **09** |

## Blocos
- **74HC194-B (PL):** guarda B no início e vira o nibble baixo do produto ao deslocar.
- **74HC194-Acumulador (PH):** nibble alto do produto. O Co do 283 entra como o bit mais alto depois do deslocamento.
- **74HC08 + 74HC283-22:** o 08 faz "A só passa se o bit de B for 1" e o 283 soma ao PH.
- **74HC194-A-REG:** guarda A no início do ciclo, para A não mudar no meio da conta.
- **74HC194-Resultado-Alto / Resultado-Baixo:** guardam o produto pronto e alimentam os displays, que nunca mostram valores parciais.
- **Contador (74HC194-CONTADOR + 74HC283-INC):** o 194 carrega todo clock a saída do 283, que soma +1. Isso conta de 0 a 15, um ciclo de **16 clocks**.
- **Controle (74HC283-NOT, 74HC283-GO e 74HC08-ACT):** o 283 faz o papel de NOT e de OR (um bit em 5V dá o inverso; bits em zero separam as "portas" para o carry não vazar). O 74HC08-ACT gera os sinais de passo (`ACT`) e de cópia do resultado (`STB`). O 74HC08-PH-ZERA zera o PH de forma síncrona.

O 74HC194 tem 4 modos, dados por S1 e S0: 00 mantém, 01 desloca à direita, 10 desloca à esquerda e 11 carrega.

## Ciclo de 16 clocks (contador K = 0..15)
- **K = 15:** carrega B no PL, zera o PH e guarda A (sinal `RCO`, o Co do contador).
- **K = 0 a 3:** os 4 passos de soma e deslocamento (`ACT`).
- **K = 4 a 14:** tudo parado, produto pronto.
- **K = 8 a 11:** o produto é copiado para os registradores de resultado (`STB`).

Depois de mudar A ou B, o resultado novo aparece em até uns 32 clocks (cerca de 32 ms a 1 kHz). Logo após ligar, o display pode mostrar um valor qualquer por um instante.

## Testes
- Conferi 2×2 = 04, 2×8 = 10 (16 decimal) e 15×15 = E1.
- Todas as 256 combinações de 4×4 também foram conferidas numa simulação à parte.

## Arquivo
`multiplicador_4x4_automatico.sim1` (salvo no SimulIDE 1.1.0-SR2, clock de 1 kHz)

---
Feito por mim (Vittin019)
