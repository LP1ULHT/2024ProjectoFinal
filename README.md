# Projecto Final 2024

**UNIVERSIDADE LUSÓFONA DE HUMANIDADES E TECNOLOGIAS**

*Linguagens de Programação I*

# Projecto Final 2024 - Mortal Pandora C_ombat
![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/0f0cd02f-d91b-4551-bd2e-bfa1e9bee2ad)



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

Além disso, dependendo de sua estamina, o jogador pode activar um *combo*, que é um ataque que causa um número significativo de danos e consome mais estamina.

Como ataque especial, quando um jogador estiver a perder, é possivel andar no tempo para trás, onde retrocedemos o jogo um certo número de ataques.

## Requisitos do jogo

---
### Core
---

**Requisito 1.**
Cada jogador começa com 1000 pontos de vida e 1000 pontos de estamina. Um jogador nunca pode ter mais do que 1000 pontos de vida e 1000 pontos de estamina.

**Requisito 2**
O jogador vence quando o seu oponente tem pontos de vida nulos ou negativos. Neste caso, o jogo termina.

**Requisito 3**
OS jogadores podem empatar quando obtêm ao mesmo tempo pontos de vida nulos ou negativos. Neste caso, o jogo termina.

**Requisito 4**
O número de jogadores é sempre 2.

**Requisito 5**
Um jogador pode realizar até 4 ataques em cada jogada (não pode escrever mais de 4 caracteres).

**Requisito 6**
Um jogador pode realizar apenas 1 combo em cada jogada (neste caso, escreve mais de 4 caracteres).

**Requisito 7**
Não se pode combinar ataques com combos.

**Requisito 8**
Cada jogador faz uma jogada por vez, alternando suas tentativas.

---
### Ataque e Combos
---

**Requisito 9**
Existem os seguintes ataques correspondentes a uma letra conforme a seguinte tabela:


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
| Murro | M |
| Defender | D |
| Descansa | |

**Requisito 10**
O jogo rege sob efeito "Pedra, Papel, Tesoura", isto é, um ataque tem um determinado efeito de acordo com ataque do outro jogador. Os efeitos sao descritos na seguinte tabela.
![Screenshot 2024-05-16 001812](https://github.com/LP1ULHT/2024ProjectoFinal/assets/1611372/aa6eab03-e46b-488c-89d6-07e86430d2b6)

Se valor é positivo jogador1 tira esse valor positivo em pontos à vida do jogador 2
Se valor é negativo jogador2 tira esse valor positivo em pontos à vida do jogador 1

**Requisito 11**
Se numa jogada o jogador nao escrever 4 letras, as letras em faltas são assumidas que o jogador está a fazer o *Descansa*

- Exemplo: Se o jogador escrever só as duas letras *"BC"*, deve ser lido como a sequencia *Bicada, Cotevelada, Descansa, Descansa*.
         
**Requisito 12**
Cada ataque efectuado pelo jogador faz perder 25 pontos de estamina (com exceção do *Defender* e *Descansar*). O valor mínimo da estamina é zero. O jogador pode continuar a realizar ataques mesmo com estamina a zero. 

**Requisito 13**
À medida que a estamina diminui, o jogador perde mais vida ao sofrer ataques do oponente, de acordo com a seguinte lógica:

 - **Estamina > 750** - Perde vida que é descrita na tabela do Requisito 10
 
 - **Estamina > 500** - Perde **dobro** da vida que é descrita na tabela do Requisito 10
 
 - **Estamina > 250** - Perde **triplo** da vida que é descrita na tabela do Requisito 10 

 - **Estamina < 250** - Perde **quadruplo** vida que é descrita na tabela do Requisito 10 

*Combos não são afetados pelo fator multiplicativo.*

**Requisito 14**
Quando um jogador utilizar o ataque *Defender*, ele gasta 10 pontos de estamina e recupera 10 pontos de vida.

**Requisito 15**
Quando um jogador utilizar o *Descansar* (ao não preencher letras), ele recupera 25 pontos de estamina. 
O *Descansar* não pode ser realizado diretamente. 
Ele só é realizado quando há uma diferença de número de ataques (pelo jogador com um menor número de ataques no turno).

- Exemplo: jogador1 usa *"AA"* e o jogador2 usa *"Z"*. Deve-se considerar que o jogador2 utilizou uma *Zarabatana* e um *Descansar*.

**Requisito 16**
O jogador pode ativar combos durante o jogo, quando certas sequências de letras forem escritas. 
Um ataque combo faz o jogador gastar estamina. 

As combinações e os pontos que reduzem a vida/estamina do oponente são mostrados abaixo:

| Nome do Combo | Sequência de Letras | Pontos Vida Tirado ao oponente | Estamina Perdida |
| --- | --- | --- | --- |
| Arrozão | ARROZAO | 500 | 500 |
| Dad Bad | DADBAD | 400 | 400 |
| Bife Wellington | STTEACC | 300 | 300 |
| Furacão Thiago | TATAPAAA | 200 | 200 |

**Requisito 16.1**
Um jogador só pode fazer um combo quando tem mais do que 750 de estamina. 

**Requisito 16.2**
Existe um combo especial chamado *Lucio Tarzan Reversal*, que é ativado quando as letras *"TARZANTABORDA"* são escritas. Este combo permite que o jogador retroceda no tempo, revertendo o jogo para X ataques anteriores, onde X é o número especificado pelo jogador.

- Exemplo: Se o jogador quiser retroceder 3 ataques, ele escreve "TARZANTABORDA3".

*O conceito por trás disso é apagar os X últimos elementos da lista ligada, forçando cada elemento da lista a conter o valor da vida e da estamina do jogador.*

**Requisito 16.3**
Se o valor X de ataques é superior ao numero maximo que jogadas ocorridas, o jogo volta para o início.

**Requisito 16.4**
O jogador só pode fazer o combo especial *"TARZANTABORDA"* quando a estamina for maior que 500 e menor que 900.

**Requisito 17**
Caso haja uma quantidade diferente de ataques entre os jogadores, os ataques não explicitados devem ser considerados como *Descansar*. Isso inclui o caso do combo.

- Exemplo 1: o jogador1 usa *"AAO"* e o jogador2 usa *"ZZ"*. Como o jogador1 usou mais ataques que o jogador2, deve-se considerar que a *Onda de Choque* do jogador1 foi respondida com um *Descansar* pelo jogador2. No total serão realizados 3 ataques no turno.

- Exemplo 2: jogador1 usa *"DADBAD"* (um combo) e jogador2 usa *"MZZZ"*. O jogador1 usou um combo (e não pode usá-lo com outros ataques) e o jogador2 usou quatro ataques.
Deve-se descartar todos os ataques do jogador2. Considerar que o combo DADBAD do jogador1 foi respondida por um *Descansar* do jogador2.

- Exemplo 3: Se os dois jogadores usarem um combo, o resultado é que o efeito do combo ocorrer para os dois jogadores. Se o jogador1 usar o *"DADBAD"* e o jogador2 usar o *"DADBAD"*, ambos os jogadores vão perder 400 de estamina e 400 pontos de vida.

---
### Implementação
---

**Requisito 18**
O histórico de ataques realizados, pontos de vida e pontos de estamina de cada jogador é obrigatoriamente guardado numa lista ligada.

**Requisito 19**
Antes de um jogador fazer sua jogada, os últimos 20 ataques realizados pelo jogador são impressos no ecrã.

**Requisito 20**
Antes de um jogador fazer sua jogada, os pontos de sua vida e estamina são impressos.

**Requisito 21**
Se o utilizador escrever algo inválido ou fora destes requisitos, deve escrever "Ataque inválido, tente novamente" e pedir novamente a jogada.

**Requisito 22.**
Pode se inserir as jogadas por um ficheiro, onde TBD

**Requisito 23**
Cada linha do ficheiro representa uma jogada tal como descrito no requisito 5, 6, 8 e 16.

**Requisito 24**
Cada linha do ficheiro impar corresponde a uma jogada do jogador 1, e cada linhar par a uma jogada do jogador 2.

**Requisito 25**
O jogo contém os seguintes códigos secretos que, quando escritos, produzem os seguintes efeitos:

Modo-Jesus - Reinício do jogo, ambos os jogadores voltam a ter estamina a 1000 e vida a 1000.

Alt-F4 - Jogador 1 - Restaura a estamina a X pontos.

Kebab - Jogador 2 - Restaura a estamina a X pontos.

Hiroshima - Jogador 1 - Restaura a vida a X pontos.

Nood-Mode - Jogador 2 - Restaura a vida a X pontos.

---
### Exemplos

O programa imprime 3 linhas por cada jogador:

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/5f89d93d-7755-4529-b3b2-a83feca8d21f)

## Exemplo da pontuação
Cada jogador escreve os 4 ataques ou combo após aparecer as letras **I:**, depois de ambos inserirem é impresso as parelhas de ataques como mostrado em baixo.

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/a0819d99-e436-4c08-9304-99741b2d9a2e)


No exemplo acima:

- O jogador1 (P#1) insere os ataques "DADA", tem 452 pontos de vida e 825 estamina.
       
- O jogador2 (P#2) insere os ataques "BABA", tem 976 pontos de vida e 315 estamina, como estamina ja é menor que 500 perde triplo de vida
       
Assim obteve-se os pares: 

-  D vs B

         P#1 defende, logo ele gasta 10 pontos de estamina e recupera 10 pontos de vida.

         A estamina P#1 passa de 825 para 815 e a vida de passa de 452 para 462. 

         O P#2 gasta 25 de estamina, passa de 315 para 290 de estamina

-  A vs A
  
           Da zero na tabela.
  
           Estamina de P#1 passa de 815 para 790.
   
           Estamina de P#2 passa de 290 para 265.
   
-  D vs B

         P#1 defende, logo ele gasta 10 pontos de estamina e recupera 10 pontos de vida.
  
         A estamina de P#1 790 para 780 e a vida passa de 462 para 472.

         O P#2 gasta 25 de estamina, passa de 265 para 240 de estamina
   
-  A vs A

         Dá zero na tabela.
   
         Estamina de P#1 passa de 780 para 755.
   
         Estamina de P#2 passa de 240 para 215. 

Sendo assim:

         P#1 ficou com 472 de vida e 755 de estamina
         
         P#2 ficou com 976 de vida e 215 de estamina

Sendo assim quando se faz a proximas jogadas de P#1 e P#2 aparece o seguinte:

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/a04c484e-ee31-450c-952b-61d70f7257f2)



## Exemplos do jogo simples

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/08a03d16-3403-4512-887e-3b981b30161c)

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/f8b5d0d6-0599-4012-904d-9f9fc7404f9c)

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/32ff97ba-9842-4c52-968d-5f7e6f783306)


## Exemplos do jogo com combos

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/9a5e04dc-94f9-4b3d-a252-c72ace019c60)

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/a7487330-27c5-4204-95ad-526855c034ed)



## Exemplos do jogo com *Lucio Tarzan Reversal*
Anda 99 ataques para tras... o historico de ambos jogadores é totalmente apagado.

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/a1343352-5600-4949-9422-d4ed0f94edd2)

Anda 5 jogadas para tras, perde o historico das 5 ultimas jogadas

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/50b13275-fcd1-41d9-8db4-0816fe18f45d)



## Exemplo do ficheiro

Para executar com um ficheiro o programa deve aceitar um segundo parametro com nome do ficheiro.
O output esperado é exatamente o mesmo, apos o **"I:"** deve se fazer printf da linha do ficheiro escrito.

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/2b68589b-49df-4f98-88a7-2f93a6de90a7)


Conteudo do ficheiro:

![image](https://github.com/LP1ULHT/2024ProjectoFinal/assets/98768479/1eaca41a-cee9-4aa7-bf12-27e3e2e187b7)
