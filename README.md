# Projecto Final 2024

**UNIVERSIDADE LUSÓFONA DE HUMANIDADES E TECNOLOGIAS**

*Linguagens de Programação I*

# Projecto Final 2024 - Street Pandora C_ombat
>Na resolução deste projecto deve ser utilizada a Linguagem de Programação C. Para além da correta implementação dos requisitos, tenha em conta os seguintes aspetos:
>- O código apresentado deve ser bem indentado. 
>- O código deve compilar sem erros ou *warnings* utilizando o *gcc* com as seguintes flags:
>- `-g -Wvla -Wall -Wpedantic -Wextra -Wdeclaration-after-statement`
>- Tenha em atenção os nomes dados das variáveis, para que sejam indicadores daquilo que as mesmas vão conter.
>- Não é permitida a utilização de variáveis globais ou estáticas
>- O programa não deve ter *memory leaks*.
>- O trabalho deve ser desenvolvido e submetido de forma individual.

>Este exercício deverá ser submetido na plataforma Pandora até às 23h59 de dia 18 Junho e será contabilizado para a nota final da unidade curricular de acordo com os critérios disponibilizados na página da disciplina, concretamente nos slides da primeira aula.

>Todos os trabalhos serão comparados utilizando um sistema de deteção de plágio.
>Todos os trabalhos serão revistos e submetidos a avaliação oral

## Descrição do problema
Neste projeto, vamos implementar um jogo de luta simples em linguagem C, onde dois jogadores irão confrontar-se num épico cenário de porrada da grossa. 
Cada jogador terá a oportunidade de escolher um conjuntos de ataques em cada rodada, mas também terá de gerir a sua estamina. 

Além disso, ao executar uma sequência específica de ataques, o jogador ativa um combo que é um golpe especial que o número significativo de danos.

Como opção especial, quando um jogador estiver a perder, tem um golpe especial que permite andar no tempo para trás, onde retrocedemos o jogo um número de ataques atrás.

## Requisitos do jogo

**Requisito 1.**
Cada jogador começa com 1000 pontos de vida e 1000 pontos de estamina.

**Requisito 2.**
O jogador vence quando seu oponente tem pontos de vida negativos.

**Requisito 3.**
O número máximo de jogadores é 2.

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

**Requisito 10.**
O jogador só pode fazer um combo quando estamina for maior que 750

**Requisito 11.**
O jogador só pode fazer o combo especial *TARZANTABORDA* quando estamina é 1000

**Requisito 12.**
Cada jogador faz uma jogada por vez, alternando suas tentativas.

**Requisito 14.**
O número máximo de jogadores é 2.

**Requisito 15.**
O histórico de golpes efectuados, pontos de vida e pontos de estaminda de cada jogador é obrigatórimente guardado numa lista ligada. 

**Requisito 16.**
Um jogador pode realizar até 4 ataques em cada jogada

**Requisito 17.**
Um jogador pode realizar só  1 combo em cada jogada

**Requisito 18.**
Não de pode combinar ataques com combos

**Requisito 19.**
Antes de um jogador fazer sua jogada, os últimos 40 ataques realizados pelo jogador são impressos no ecrã.

**Requisito 20.**
Antes de um jogador fazer sua jogada, os pontos de sua vida e estamina são impressos


