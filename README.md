# 2024ProjetoFinal

Escreva o programa em C que atenda aos seguintes requisitos.

## Requisitos do jogo

**Requisito 1.**
Cada jogador começa com 1000 pontos de vida e 1000 pontos de estamina.

**Requisito 2.**
O jogador vence quando seu oponente tem pontos de vida negativos.

**Requisito 3.**
Um jogador pode realizar até 4 ataques em cada jogada.

**Requisito 4.**
Existem os seguintes ataques corresponde a uma letra conforme a seguinte tabela:

| **Nome do Ataque** | **Letra** |
| --- | --- |
| Zarabatana | Z |
| Pontapé | P | 
| Agarrar | A | 
| Estalada | E |
| Tombeta | T |
| Rasteira | R |
| Cotovelada | C |
| Bicada | B | 40 |
| Onda de Choque |
| Defender | D |

**Requisito 5.**
Quanto mais ataques um jogador fizer em uma jogada, mais estamina será consumida, conforme a seguinte tabela:

| Número de Ataques | Estamina Consumida |
| --- | --- |
| 1 Ataque | -10 |
| 2 Ataques | 10 |
| 3 Ataques | 30 |
| 4 Ataques | 100 |

Se fizer só um ataque, o jogador recupera 10 pontos de estamina.

**Requisito 6.**
À medida que a estamina diminui, os ataques do jogador causam menos dano ao oponente, de acordo com a seguinte tabela:

| **Nome do Ataque** | **Letra** | **Estamina > 750** | **Estamina > 500** | **Estamina > 250** | **Estamina < 250** |
| --- | --- | --- | --- | --- | --- |
| Zarabatana | Z | 12 | 9 | 6 | 3 |
| Pontapé | P | 16 | 12 | 8 | 4 |
| Agarrar | A | 20 | 15 | 10 | 5 |
| Estalada | E | 24 | 18 | 12 | 6 |
| Tombeta | T | 28 | 21 | 14 | 7 |
| Rasteira | R | 32 | 24 | 16 | 8 |
| Cotovelada | C | 36 | 27 | 18 | 9 |
| Bicada | B | 40 | 30 | 20 | 10 |
| Onda de Choque | O | 44 | 34 | 22 | 11 |
| Defender | D | 0 | 0 | 0 | 0 |

**Requisito 7.**
Quando um jogador usar o ataque Defender, ele recupera 30 de estamina e 20 pontos de vida.

**Requisito 8.**
O jogador pode ativar combos especiais durante o jogo, quando certas sequências de letras forem escritas. As combinações e os pontos que reduzem a vida do oponente são mostrados abaixo:

| Combo | Letras | Pontos |
| --- | --- | --- |
| Arrozão | ARROZAO | 500 |
| Dad Bad | DADBAD | 400 |
| Wellington Steak | STTEACC | 300 |
| Furacão Thiago | TATAPAAA | 200 |


**Requisito 9.**
Existe um combo especial chamado "Lucio Tarzan Reversal", que é ativado quando as letras *TARZANTABORDA* são escritas. Este combo permite que o jogador retroceda no tempo, revertendo o jogo para X ataques anteriores, onde X é o número especificado pelo jogador.

Exemplo:
Se o jogador quiser retroceder 3 ataques, ele escreve TARZANTABORDA3.

*O conceito por trás disso é apagar os X últimos elementos da lista ligada, forçando cada elemento da lista a conter o valor da vida e da estamina do jogador.*

**Requisito 12.**
Antes de um jogador fazer sua jogada, os últimos 40 ataques realizados pelo jogador são impressos.

**Requisito 14.**
O número máximo de jogadores é 2.

**Requisito 15.**
Cada jogador faz uma jogada por vez, alternando suas tentativas.
