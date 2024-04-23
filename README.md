# 2024ProjectoFinal

Escreve o programa em C que cumpre os seguintes requisitos.

##Requisitos do jogo

*Requisito 1.*

Cada jogador tem 1000 pontos de vida e 1000 pontos de estamina

*Requisito 2.* 

Ganha o jogador que levar o oponente ter os pontos de vida com valor negativo.

*Requisito 3.* 

Um jogador pode em cada jogada dar até 4 golpes. 

*Requisito 4.* 

Um golpe corresponde a uma letra, que retira pontos ao oponente de acordo com a seguinte tabela:

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

*Requisito 5.*

Quanto mais golpes o jogador fizer por jogada, mais estamina consome de acordo com a seguinte tabela:

| Número de<br><br>Golpes | Estamina<br><br>Consumida |
| --- | --- |
| 1 Golpe | \-10 |
| 2 Golpes | 10  |
| 3 Golpes | 30  |
| 4 Golpes | 100 |

*Requisito 6.*

À medida que estamina diminui o jogador começa a retirar menos pontos ao oponente de acordo com a seguinte tabela:

| **Nome do Golpe** | **Letra** | **Estamina >750** | **Estamina >500** | **Estamina >250** | **Estamina < 250** |
| --- | --- | --- | --- | --- | --- |
| Zarabatana | Z   | 12  | 9   | 6   | 3   |
| Pontapear | P   | 16  | 12  | 8   | 4   |
| Agarrar | A   | 20  | 15  | 10  | 5   |
| Estalada | E   | 24  | 18  | 12  | 6   |
| Tombeta | T   | 28  | 21  | 14  | 7   |
| Rasteira | R   | 32  | 24  | 16  | 8   |
| Cotovelada | C   | 36  | 27  | 18  | 9   |
| Bicada | B   | 40  | 30  | 20  | 10  |
| Onda de Choque | O   | 44  | 34  | 22  | 11  |
| Defender | D   | 0   | 0   | 0   | 0   |

*Requisito 7.* 

Quando o jogador usar o golpe Defender recupera 30 de estamina e 20 pontos de vida.



*Requisito 8.* 

O jogador pode ativar golpes especiais chamados combos durante o jogo, isto acontece as seguinte letras já terem sido escritas . As combinacões e pontos que retiram do oponente é mostrado de seguiga

| Combo | Letras | Pontos |
| --- | --- | --- |
| Arrozão | ARROZAO | 500 |
| Dad Bad | DADBAD | 400 |
| Wellington Steak | STTEACC | 300 |
| Furacão Thiago | TATAPAAA | 200 |

Exemplo:
ARROZAO é composto por 2 letras A, 2 letras R, duas letras O e uma letra em baixo esta duas sequencias de letras onde o combo foi ativado

--> ST**R**D**A**C**OR**DD**A**PE**OZ**

O conceito por detrás és as letras estarem numa lista ligada, o programa em C procura se a letras estão la presentes.


*Requisito 9.* 

Existe um combo especial que é o **Lucio Tarzan Reversal**", isto acontece as *TARZANTABORDA* letras já terem sido escritas, este combo permite o jogador andar no tempo para trás, revertendo o jogo para X golpes antes. Isto é util se ele tiver prestes a perder. 

Exemplo:
Se tiver o combo ativar e quiser andar para o jogo 3 golpes (letras) atrás ele escreve
TARZANTABORDA3

O jogador so pode andar no maximo 9 golpes (letras) para tras com este combo.

O conceito por detras é apagar X ultimos elementos da lista ligada, isto força tambem, cada elemento da lista contenha o valor da vida e estamina do jogador.


*Requisito 10.*
O jogador pode ativar multiplos combos e decide os aplicar quando quiser.
Para aplicar o combo, o jogador volta escrever a sequência de carateres


*Requisito 11.*
A letras são gravadas na lista ligada, tem procurar os combos na lista, e quando acontece apagar essas letras.


*Requisito 12*
Antes do jogador fazer a jogada é impresso os ultimos 40 golpes efectuados pelo jogador

*Requisito 13*
Quando se executa o combo *TARZANTABORDA* recupera o estamina e vida, de N golpes atrás, mas não se recupera os combos usados. 
Logo elementos apagados da lista ligada não são necessárias serem recuperadas.

*Requisito 14*
Numero máximo de jogadores é 2

*Requisito 15*
Cada jogar faz uma jogada de cada vez, alternando suas tentativas.
