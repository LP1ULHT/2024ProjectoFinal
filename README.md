# Projecto Final 2024

**UNIVERSIDADE LUSÓFONA DE HUMANIDADES E TECNOLOGIAS**

*Linguagens de Programação I*

# Projecto Final 2024 - Street Pandora C_ombat

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/43f09cab-9b86-4523-a9e0-20cd7d4bd8e9)


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
Cada jogador terá a oportunidade de escolher um conjunto de ataques em cada rodada, mas também terá de gerir a sua estamina. 

Além disso, dependendo de sua estamina, o jogador pode activar um "combo", que é um ataque que causa um número significativo de danos.

Como ataque especial, quando um jogador estiver a perder, é possivel andar no tempo para trás, onde retrocedemos o jogo um certo número de ataques.

## Requisitos do jogo

**Requisito 1.**
Cada jogador começa com 1000 pontos de vida e 1000 pontos de estamina.

**Requisito 2.**
O jogador vence quando seu oponente tem pontos de vida nulos ou negativos. Neste caso o jogo termina.

**Requisito 3.**
O número máximo de jogadores é 2.

**Requisito 3.1.**
Um jogador pode realizar até 4 ataques em cada jogada (nao pode escrever mais de 4 caracteres).

**Requisito 3.2**
Um jogador pode realizar só 1 combo em cada jogada (neste caso escreve mais de 4 caracteres).

**Requisito 4.1**
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
| Bicada | B | 
| Onda de Choque | O |
| Defender | D |
| Descansa | (espaço em branco)|

**Requisito 4.2**
*O jogo rege sob efeito "Pedra, Papel, Tesoura", isto é, um ataque tem um determinado efeito de acordo com ataque do outro jogador. Os efeitos sao descritos na seguinte tabela.*


![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/178c41bc-316b-48de-b35e-21189764bcac)


Se valor é positivo jogador1 tira esse valor positivo em pontos à vida do jogador 2
Se valor é negativo jogador2 tira esse valor positivo em pontos à vida do jogador 1

**Requisito 4.3**
Se numa jogada o jogador nao escrever 4 letras, é assumido que as letras não escritas são espaços em branco que é equivalente fazer o *Descansa*

Exemplo: Se o jogador escrever só as duas letras *BC*, deve ser lido como a sequencia *Bicada, Cotevelada, Descansa, Descansa*.


**Requisito 5.**
*Cada ataque efectuado pelo jogador faz perder 25 pontos de estamina*

**Requisito 6.**
*À medida que a estamina diminui, o jogador faz menos ataques por jogada*

| **Estamina > 750** | 4 ataques |
| **Estamina > 500** | 3 ataques |
| **Estamina > 250** | 2 ataques |
| **Estamina < 250** | 1 ataque |

**Requisito 7.**
*Quando um jogador usar o ataque Defender, ele recupera 50 pontos de estamina e 50 pontos de vida.*

**Requisito 7.**
*Quando um jogador usar o Descansa, ele recupera 100 pontos de estamina.*

**Requisito 8.**
O jogador pode ativar combos durante o jogo, quando certas sequências de letras forem escritas. As combinações e os pontos que reduzem a vida do oponente são mostrados abaixo:

| Nome do Combo | Sequência de Letras | Pontos |
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
*O jogador só pode fazer o combo especial *TARZANTABORDA* quando estamina é maior que 800 e menor que 900*

**Requisito 12.**
Cada jogador faz uma jogada por vez, alternando suas tentativas.

**Requisito 14.**
O histórico de ataques efectuados, pontos de vida e pontos de estamina de cada jogador é obrigatórimente guardado numa lista ligada. 

**Requisito 15.**
Não de pode combinar ataques com combos

**Requisito 16.**
Antes de um jogador fazer sua jogada, os últimos 40 ataques realizados pelo jogador são impressos no ecrã.

**Requisito 17.**
Antes de um jogador fazer sua jogada, os pontos de sua vida e estamina são impressos

**Requisito 18.**
Se o utilizador escrever algo invalido ou fora destes requisitos, deve escrever "Ataque invalido, tente de novo" e pede de novo a jogada.

**Requisito 19.**
Quando um jogador aplica um ataque combo ele gasta 500 pontos de estamina

**Requisito 20.**
O valor maximo de pontos de estamina é 1000

**Requisito 21.**
O valor maximo de pontos de vida é 1000

## Exemplo da pontuação


## Exemplos do jogo
Brevemente...
