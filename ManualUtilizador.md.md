---


---

<h1 id="inteligência-artificial---adji‒boto">Inteligência Artificial - Jogo do Cavalo</h1>
<h2 id="manual-de-utilizador">Manual de Utilizador</h2>
<h3 id="acrónimos-e-convenções-usadas">Acrónimos e convenções usadas</h3>
<p><strong>Lista:</strong>  Conjunto de valores envolvidos por parêntesis. Ex.: ( a b c )<br>
<strong>Nó:</strong> Estrutura de dados que guarda informação do jogo actual, nomeadamente o estado do tabuleiro actual, valores heurísticos e o seu nó antecessor.<br>
<strong>
Heurística:</strong> Cálculo para atribuir um valor concreto a um nó.<br> 
Ex.: h = número de peças existentes no tabuleiro</p>
<p>

De notar, em LISP as funções são chamadas da seguinte forma:<br>
<code>(&lt;funtion&gt; &lt;arg1&gt; &lt;arg2&gt;)</code></p>
<h3 id="introdução">Introdução</h3>
<p>
Este manual tem como objectivo guiar o utilizador para que consiga proceder à utilização do programa. O jogo do Cavalo consiste numa variante do problema matemático, Passeio do Cavalo. Desenvolvido através da linguagem LISP no âmbito da cadeira de Inteligência Artificial - Licenciatura em Engenharia Informática do Instituto Politécnico de Setúbal 2019/12.<br>
O jogo toma lugar num tabuleiro parecido com o do Xadrez, mas este tem 10 linhas e 10 colunas (em vez de 8x8). O objetivo do jogo é controlar uma peça com os mesmos movimentos que o cavalo do Xadrez, e visitar todas as casas do tabuleiro, cada uma com diferente pontuação.  Enquanto que no jogo normal são necessários dois jogadores, cada um com uma peça em lados opostos do tabuleiro, esta versão é jogada apenas por um.  Sendo assim, o objetivo será atingir uma certa pontuação utilizando vários algoritmos diferentes.<br>
O programa inicia com um tabuleiro escolhido pelo utilizador, um algoritmo de procura também escolhido pelo utilizador e  de seguida é pedida uma pontuação alvo. No final, este devolve visualmente todas as jogadas efetuadas que levaram à solução, ou seja, foi atingida a pontuação pretendida pelo utilizador. Caso não seja possível atingir o objetivo, o problema diz-se não ter solução. </p>
<p>

No decorrer do programa é possível visualizar todos os tabuleiros disponíveis, "correr" um jogo com um tabuleiro e algoritmo escolhidos pelo utilzador, qual a heurística a utilizar, e no final, analisar os resultados obtidos após chegar à solução.</p>

<h3 id="instalação-e-utilização">Instalação e Utilização</h3>
É necessário que a directoria seja criada em  C:\IA_2, e lá sejam colocados os ficheiros do programa:</p>
<ul>
<li>
  interact.lisp</li>
<li>
  jogo.lisp</li>
<li>
  algoritmo.lisp</li>

</ul>
<p>

Recomenda-se a utilização do IDE lispWorks. Para iniciar o programa deve compilar no IDE o ficheiro <em>*jogo.lisp</em>* e de seguida executar a função *start*, como mostra a imagem:</p>

![START](https://lh3.googleusercontent.com/gofbx8rdOsj9f4bjZTWHA6YO_JwnXepLz_iLCGaH60tRYOw11GYd8ZJWjwq4nkMkLn0jNDIms-CGCvw1372XaxKOb0vaWsqV0CZpiTM4Co4mCesMwYqGtpX6hpRGeSDYGkkIapIv64K74mbm8mLzdpAgwDpgXirZ-0VdnotBoztn6av4DlNJtHJsc7VL7pEZlVEG5RtqB1bQNT9KwPsNNLC5qLaTLgophsGfxGlZ9QY7TXLy1nBeSsAeeLRRO32WrN74L8h6cnktjTefcestRHuxZ24B1rLNBvltatIeLSiudPdwHhS3a8cSrE0e-pIHqVz6vFgpVGkgvjbnEcv4MhrO_tqc-ZBcZOr2EauuKMjB_vtAprcacJR2I82bOHFe_1WXB81mq1xQ48UI9p9vM1oEbI_IALm8zSYG3KZWOc-q3z4AeH3LUjxnB-EXwN5PieqDXO-cbFegZj4Pwer3nK4gIX-0R4QVTc-76ZjmVw-zk9gsADNVxpWSlWvj9lAgqIyQYzHhjToOe7rXlqdO17oBE-BbqHKESLII7sAEMpUr7x_VW9tgjkjhSStDrsvd77UxBJcbwyLCKfN4GHQ-Oprpapr8yrhFq7RSJP_2JY9el-JsnKB2wTmy35ivVdhyz9KnGHJYY66YNMN2NXgfAQku_YYARXLp_Lj0Uxv2uW8GKSJT=w421-h377-no)
<p>
Para navegar os menus terá de escrever os números pretendidos.</p>

<h3 id="input">Input</h3>Além do início do programa através da função <em>start</em>, todo o input directo no programa é efectuado apenas com os algarismos correspondentes ás acções do menu actual, incluindo as escolhas das jogadas possíveis durante um jogo.  No que diz respeito ao jogador humano, o programa lê a jogada inserida através do teclado (ex. 1 - (1 A)).

<h3 id="outputs">Modos de Jogo</h3>
Existem apenas 2 modos de jogo por selecionar:
<ol>
<li>Humano vs Computador</li>
<li>Computador vs Computador</li>
</ol>
No início de cada partida, o utilizador deve decidir quem começa, humano ou computador, e qual o tempo limite para o computador jogar, o qual será de X milissegundos. O valor de X deverá ser um valor compreendido entre 1000 e 5000 milissegundos.

![CONFIGS](https://lh3.googleusercontent.com/_SrI2YyR0cnWZBZCUehnUe0kO3hWOEArClO-XWUlvCbbuZcaXcTNMoVPDu0o8XZv_pX-NEZtguZC1QtGptfnyAZYFNyRjcqF0KZCgstm1vJjQDI7QQWs_H2IxISTdgXPIDwrEDmFk_hibLRhPZDgx1aairt4uecDyj0iRxDCYC9qUU_v-vbmVhrhvqBjPeZHGNvSng6y4jAT5_6l1XeLZlpHt3gj1lxMA2DgDLWDw07plKatqUb819Tu05if2iTCgxBcFRah4uNMKRU_p_2qCpFX1poti5iH1xseBzXBn9HBxvaw9VkCZdy9VO7tEugN8i5NcyiSJSBiCIKPWZBpYC5Gc5vzWsns7bWRPDyWa8iyGJLwalv1yrKJbf-9lJzqiSax-tpsZDqjGqbADBoBsbUpyC3Mwih22NzmS30Z5gVJJkBMEi3api0CSMBRSyQhr0ax4zUHA1QE19sgW69OncaOwJx1NtOFtYUxuctdveIU3iZhxkiqb0tOfQwBbcP7HuEwl_wqC3iz8WY_ocF9YmUwJOW-FQ0wetiSG2iWsVE203OC3DG5C0RiK2KEC7gxPcV86kTBSFMhI3E5yIICR7eqgunP7MjxNpeApMGp4h13ebRSaafo3VyNap3tnk5mBjSdmLQrMha3mcGs8OiXntb_6es3LXkLUOz-DXuLznci4BUB=w451-h629-no)

O jogo é iniciado pelo Jogador 1 colocando o cavalo branco na casa de maior valor na 1ª linha do tabuleiro. O processo é análogo para o Jogador 2, que coloca o cavalo preto na casa de maior valor da 10ª linha do tabuleiro. A cada jogada, mediante a casa em que se colocou o cavalo, é aplicada a regra do número simétrico ou a regra do número duplo. Caso um dos jogadores não consiga movimentar o cavalo, cede a vez ao jogador oposto. O jogo termina quando nenhum jogador consegue movimentar o cavalo.
<h3 id="outputs">Outputs</h3>

<p>
Após o fim de cada jogada é apresentado o tabuleiro com as pontos de cada casa e as posições das peças atuais.</p>

![enter image description here](https://lh3.googleusercontent.com/hJD5twRuby06JjpHcCXa5QY6aVUMLciBQCsXHxIN5VY3wkzeuDrp6TOP3kk9L0O1Cgcc5GbdBXHpg32-zUbV4uA8upPQW5MCOxx2N3Q1kTtZ_M2ekxkU-ZWa_0x6iyiH7WZ2kheOvbd2CiHYeBi_zQHjv2jO7TO75zxFlF-NBo6PRxEJqaih6fz19WDRRmZzZmp-7TmPuJLfD90JrJxo7kGAmknWEKiW45CNuI6zO9lMappb8IKorVqZa55KIxT5HhzmE_eTWA-ZGSUB68ZvemRcQhzyxaenj41N6GrJHy9WhoygWlI6mAvLf1BbgIr5dQZBoVWl0C3bb1HIMDssw4q0ywllRKPHWH8hCL-s10VMXg5fe1sGYmfOkjKre7Evh1gnaZW7o4sCxvSVDwXyz_CamPW0q8x3ImR7N_hLriLjlNKYUQkBybsyafHU2ece_WjmEErfSGGrnBrT7DkDJ_gsOmJWXcC9qLg11bNsofPE9DEHWd2PZGCaqzjFZC0sR3IUGup5bRL9bLte9mudDTz4K6yNFbJNBPDnTAM0R5kV1QRsu8Om0MZ1NQ99Pb-TG7Rh3-TSJ-VaclC_eqHWcNL-mYkj7A7gQ3oZjt72qZYnCIBrfnM8A1Mz5FUhxwUAa4kThbvr0ZKIVodRfMmzK8gHQMBHNM9pDJDzSz5xLvVhJu1e=w372-h469-no)

Cada casa do tabuleiro poderá ser representada pelo seguinte valor: 
<ul>
<li>De 00 a 99 significa que a casa ainda não foi visitada; </li>
<li>NIL significa que a casa já foi visitada; </li>
<li>-1 significa que o cavalo branco (Jogador 1) se encontra nessa casa;</li>
 <li>-2 significa que o cavalo preto (Jogador 2) se encontra nessa casa.</li>
</ul>

Para além disso serão gravadas  o número de nós analisados, o número de cortes efetuados (de cada tipo), o tempo gasto em cada jogada e o tabuleiro atual no ficheiro <em>*log.dat</em>* na mesma directoria que o programa.



<h4 id="breadth-first-search">

#### Breadth-first Search</h4>
<p>
Algoritmo de procura em <strong>largura</strong>, completa a exploração de todos os nós existentes num nível antes de passar para os seus filhos (nível seguinte).</p>
<h4 id="depth-first-search">

#### Depth-first Search</h4>
<p>
Algoritmo de procura em <strong>profundidade</strong>, explora sempre o nó aberto mais à esquerda e só depois de esgotar o caminho mais à esquerda volta os níveis necessários atrás até encontrar o nó mais à esquerda que não seja o que já foi esgotado.</p>
<h4 id="a---informed-search">

#### A* - informed search</h4>
<p>
O algoritmo A* é um algoritmo de procura <strong>informada</strong>, que faz uso de uma dada função heurística para atribuir um valor a cada nó que é gerado e opta por explorar sempre o nó de menor valor.</p>


<h3 id="exemplo-do-programa">Exemplo do programa:</h3>

![exe1](https://lh3.googleusercontent.com/DlP_sudKFymb0ESblAbsaJ_jGVpYjYU5DJnhYlKZ1SNgA7v3FgHyJjGohdZ1-4oXL4I-cBnUe7FFh6PklXC5TZE5SrnfsFJMccN42kv56pmJAsNY6UNrKfgzYbNvX6S2RSC9Sr1zKtHmVHgmgQCsbTtMulwbLJ1s03GwozALqsv6qoTf7ayogG8KGd1XcRzZuSzlQ-0ZHOqFgNTPNGzl_SoTwSdgsxm3r-JSTtDgmko_fWIM4SD5wbEN3zxKzM0AyC2MIYgqgmYXToyOZX3hqbc8TsWQt1MctX_2j1Q1fSrcZLaGvymVF1_oAju6HrQ0r42652kIsw0C9yQwYJ9_KZAnf3ImnLjGjNgnzQMWlqdHFCwNyIAN5601uSpc-gxKnIG5dy-kRTr3kncuctY6yOOCxq4OUUhXhy8s30eRCi0JwHO35QnWkRUJreNo-MA2DSsTlCaTtDBNni1HBDa3orGRd-5mfF0Pvr0U5BZ8sSbSD1nSC0rLUVc4YVKsFEE53HC_evuO6tVSMj9U-A790douscOLoyKD-hHeYKksnLlvvbWAx6uYawoBvu-19bBLeCc-JMjm06rFk1uXXwOdfepuFRCL2DdjwcwQ0hxTLPE07zky-EPSQM3--fUxWV6YbN-1Xu4NZqR3rOvC67Mio6t3epwXm-IyBa8Gy2aXNP2RTc0C=w433-h702-no)

![exe2](https://lh3.googleusercontent.com/mx3MI-KVVKLBJpgtI8Xr_iqyLLcNpWIppFTUFWLa4axGfqrfJGlVNKj-AO9KuTD1f75q6bVISUSlMlvugM90ET_zI1PgdTPw4e1rn7oTo-ohAUpE-tvorkF9vS8E02weirorVPS1LnS_3B5djuhMq6nwsKBX1sWh32HZPjCBQeZVt5BILN24UP8BPS-YXG9UoMYJPkW7T8DHfFBQ9sUcrNQjHQZFM2M7Za8q7CaNqpk2BVXooRvF6moT9gzT2QdE4re5sCAve7Gg7e3ve13OQy517yBZ0HlNS1Hc2U7tW-aBy_j4Li5ZRqBOQA0Yb-dh59wI5BZOFOGvJWFAM1QgqJJrxHygRNFAH4ofX7YBxgoNKo52ixU76d7Xs6-w-RU9ZhMTBvhvoPE-Lusr3MJACF0AxEoF5hNEZjsRPKtFnHTwKrxjMvzA1zjJGo6ZKQLAz59lHK8-Db3-DZBG4Ysqt3vCERhAoLX60-UDtIIf7Q0AjdHL9iHH-tjxOI2aMgAisegHPAJtiYE7-DIisxDp_Jwv6S-ujg3VcFOIEWiA9oQZw9zQWKs9EQSsaCiLF30QluZryig6EHN_HsTFhxSmAH89sVnrIlY7roZfTrgMiXG1lOv_BkEY6laAU6Jf04bWC5itBrVLNGVqoB702IjU0KcrtlnEUVX7qiGUO_1TdeUJVLNF=w393-h434-no)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM5NjkxMjgyNywtNjcxNDI4ODYwLC0xNz
UzNzIwOTU1LC0xNDQ4OTczODY3LC00NTQ1MjI2OCwtNDU0NTIy
NjgsLTIxMDcwNDIyMDIsLTE5OTk3Njk0MzUsMTMzNDY0NjUwNy
w3OTQxMjQ0NzksMjExNjE2NDQ1MywtMTg3NzAyMDM3MCwtNDI3
OTYzNzAyXX0=
-->