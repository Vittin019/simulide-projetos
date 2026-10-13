# Projetos de lógica digital no SimulIDE

Circuitos de lógica digital montados no [SimulIDE](https://simulide.com/) para a disciplina de eletrônica digital: somadores, subtrator, contador e um multiplicador sequencial automático.

## Projetos

| Pasta | Projeto | CIs principais |
|---|---|---|
| [`01-somador-8bits`](01-somador-8bits) | Somador de 8 bits, entradas por chaves e resultado em hexadecimal | 74HC283 (×2), MC14495 (×7) |
| [`02-somador-subtrator-8bits`](02-somador-subtrator-8bits) | Somador/subtrator de 8 bits com lógica de overflow e de sinal negativo | 74HC283 (×2), 74HC86 (×2), 74HC08, CD4511, MC14495 (×6) |
| [`03-contador-bcd`](03-contador-bcd) | Contador decimal de dois dígitos, com botão de clock | CD4510 (×2), 74HC4511 (×2) |
| [`04-multiplicador-4x4-automatico`](04-multiplicador-4x4-automatico) | Multiplicador sequencial 4×4 totalmente automático (soma e desloca) | 74HC194 (×6), 74HC283 (×4), 74HC08 (×3), MC14495 (×4) |

## Como abrir

1. Instale o SimulIDE (os arquivos foram salvos nas versões 1.0 e 1.1 e devem abrir em versões 1.x).
2. Menu **Arquivo → Abrir** e escolha o `.sim1` da pasta do projeto.
3. Clique em **Iniciar simulação** e mude as chaves de entrada.

## Créditos e uso de IA

- Os créditos de cada circuito estão no próprio esquema (por exemplo, o somador de 8 bits traz o nome do autor numa caixa de texto).
- O multiplicador do projeto 04 começou como um circuito manual montado pelo autor; a versão automática foi desenvolvida com ajuda do Claude (IA da Anthropic), que sugeriu o algoritmo de soma e deslocamento com produto de 8 bits e a lógica de controle. Os detalhes estão no README da pasta.
