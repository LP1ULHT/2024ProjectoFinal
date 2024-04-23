# 2024ProjectoFinal

Regras

1. Cada jogador tem 1000 pontos de vida e 1000 pontos de estamina
2. Ganha o jogador que levar o oponente ter os pontos de vida com valor negativo.
3. Um jogador pode em cada jogada dar até 4 golpes
4. Um golpe corresponde a uma letra, que retira pontos ao oponente de acordo com a seguinte tabela:

| **Nome do Golpe** | **Letra** | **Pontos** |
| --- | --- | --- |
| Socar | S   | 10  |
| Pontapear | P   | 20  |
| Defender | D   | 30  |
| Esquivar | E   | 40  |
| Gancho | G   | 50  |
| Rasteira | R   | 60  |
| Cotovelada | C   | 70  |
| Joelhada | J   | 80  |
| Agarrar | A   | 0   |

1. Quanto mais golpes o jogador fizer por jogada, mais estamina consome de acordo com a seguinte tabela:

| Número de<br><br>Golpes | Estamina<br><br>Consumida |
| --- | --- |
| 1 Golpe | \-10 |
| 2 Golpes | 10  |
| 3 Golpes | 30  |
| 4 Golpes | 100 |

1. A medida que estamina diminui o jogador começa a retirar menos pontos ao oponente de acordo com a seguinte tabela:

| **Nome do Golpe** | **Letra** | **Estamina >750** | **Estamina >500** | **Estamina >250** | **Estamina > 0** |
| --- | --- | --- | --- | --- | --- |
| Socar | S   | 12  | 9   | 6   | 3   |
| Pontapear | P   | 16  | 12  | 8   | 4   |
| Defender | D   | 20  | 15  | 10  | 5   |
| Esquivar | E   | 24  | 18  | 12  | 6   |
| Tombeta | T   | 28  | 21  | 14  | 7   |
| Rasteira | R   | 32  | 24  | 16  | 8   |
| Cotovelada | C   | 36  | 27  | 18  | 9   |
| Bicada | B   | 40  | 30  | 20  | 10  |
| Agarrar | A   | 0   | 0   | 0   | 0   |

1. Quando o jogador usar o golpe Agarrar recupera 10 de estamina e 20 pontos de vida
2. O jogador pode ativar golps combos durante o jogo, isto acontece as seguinte letras já terem sido escritas . Os combos são os seguintes:

| Combo | Letras | Pontos |
| --- | --- | --- |
| PEDRO DEATH | PEDRDEAD | 500 |
| Dad Bad | DADBAD | 400 |
| Wellington Steak | STTEACC | 300 |
| Furacão Thiago | TATAPAAA | 200 |

1. Para aplicar o combo, o jogador volta escrever a sequência de carateres
2. A letras são gravadas na lista ligada, tem procurar os combos na lista, e quando acontece apagar essas letras.
