---


---

<h1 id="inteligência-artificial---adji‒boto">Inteligência Artificial - Jogo do Cavalo</h1>
<h2 id="manual-de-utilizador">Manual de Utilizador</h2>
<h3 id="acrónimos-e-convenções-usadas">Acrónimos e convenções usadas</h3>
<p><strong>Lista:</strong>  Conjunto de valores envolvidos por parêntesis. Ex.: ( a b c )<br>
<strong>Nó:</strong> Estrutura de dados que guarda informação do jogo actual, nomeadamente o estado do tabuleiro actual, valores heurísticos e o seu nó antecessor.<br>
<strong>
__Heurística:</strong>__ Cálculo para atribuir um valor concreto a um nó.<br> 
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
É necessário que a directoria seja criada em  C:\IA, e lá sejam colocados os ficheiros do programa:</p>
<ul>
<li>
  search.lisp</li>
<li>
  puzzle.lisp</li>
<li>
  project.lisp</li>
<li>
  problems.dat</li>
</ul>
<p>

Recomenda-se a utilização do IDE lispWorks. Para iniciar o programa deve compilar no IDE o ficheiro <em>*project.lisp</em>* e de seguida executar a função *start*, como mostra a imagem:</p>

![Menu Principal](https://lh3.googleusercontent.com/NHV2oJtr3jP-MVVpTN481_roMKtaeXzk0TnfLmFDN533mx4v5_n-ZMly7uqrxRpnWNrN07k-fbxtS4VrPZOaBcxO7hOUkTWmc0vZiXVdczKA-u4pwHUzsnHqabDoZza5soUzINzf7QZNk3zoXZIBEP-yTePdRyyCMTWr99sBT32uXzkxLLQ6vnsuvTqHxgm26ikwemkG_3oW226vAnqf30_3_az4kx-HdubZRYKsSoaay-0Ao_nHWUuDNBRS1x69bi4KtTTme_4bO3Rue4z1Qknn25_kWDEovVsfe0sQK-uaG9cqlpUqCOBwUx9J2tvX3_q4XvRzEj9GeCOAL2HrwRh6EhbMgnjRfJ9p__NXatADXhPvbgPQxUQMN0x-ZjfeVgT36HxgpY-mbIPtRfXFGYfxIl17ZZ-1e2GJVqmLbbMlricBucm_geuNrW7E2dk7NWglTs8Pj7CshIGCXrkiNjRl2zcXh51ec_DlDaqKX8U8lr5SwMsQhrHcv6aCcdliiQRDSWLpaJfgs4TMnD23TkopmAO_EH-RwQ4cQWPcOrqESSvGepEvffCdHSrtNz3Cqz9AzxI6OFb7DvhCmlzqmIX0BNxHZdVKP0tCqzUNIwHjXXKqazoXARSdgBwoCrF-0ZAtmx4WF2vQaKX0FA1uH-Ft_R_hBAhVCykD5Rti--S73-iut-JcCJTbfWpA3l_8Hd0E-SAsSkb6-nl1FJ-wmck1yq8gzRFAVnJlMYtPdw=w413-h239-no)

<p>
Para navegar os menus terá de escrever os números pretendidos.</p>

<h3 id="input">Input</h3>Além do início do programa através da função start</em>, todo o input directo no programa é efectuado apenas com os algarismos correspondentes ás acções do menu actual. Contudo, é possível adicionar mais tabuleiros ao programa através do ficheiro <em>problems.dat</em>, o ficheiro pode ser aberto como <em>txt</em> com o seguinte aspecto:</p>

<p><img src="

![enter image description here](https://lh3.googleusercontent.com/s8VOgA6M3vYk2ipFC9tZjOGINploonOypQVEYUlFm0j-AeERk_2i1l5frLRwkWqXTNyw5UhNOZg)" alt="enter image description here"></p>

<p>
Para adicionar um tabuleiro basta inserir como exemplificado na imagem o novo tabuleiro, no formato <code>( &lt;tabuleiro&gt; )</code>`( <tabuleiro> )` onde o tabuleiro é as duas listas correspondentes a cada lado do tabuleiro de jogo.<br>
<strong>Notas:</strong>
__Notas:__ Deixar uma linha vazia entre cada tabuleiro; Introduzir os lados do tabuleiro em linhas diferentes.</p>
<h3 id="outputs">Outputs</h3>
<p>

### Outputs

Depois de um jogo ter sido efectuado, será apresentado visualmente todos as jogadas efectuadas até à solução, e de seguida o menu inicial.</p>
<p><img src="

![enter image description here](https://lh3.googleusercontent.com/gJEk1yEfui_Gxo30DMFnpHMe1fv3uAIbVTSUl0B3SdwJFqNfuekHxKWCmgas30qEKJEx_XcAs6o" alt="enter image description here"></p>
<p>)

Para além disso serão gravadas as estatísticas e medidas de desempenho num ficheiro à parte, <em>*resultados.dat</em>* na mesma directoria que o programa. Usando a seguinte estrutura:</p>
<p><img src="

![enter image description here](https://lh3.googleusercontent.com/KN8YFzFG4n9Wh-EiNsyYnfXg7SNvkaRCPfyfanq6e6zEuXXlO1yCxAh-xAWmOkiVFU-HvdNWckg" alt="enter image description here"></p>
<p><strong>Notas:</strong></p>
<ul>
<li>)

__Notas:__
 - Número de nós gerados - número total de possíveis jogadas geradas</li>
<li>
 - Número de nós expandidos - número de tabuleiros onde se exploraram as jogadas possíveis</li>
<li>
 - Penetrância - quociente entre o comprimento da solução e o número total de nós gerados</li>
<li>
 - Comprimento da solução - número de níveis da árvore do problema desde a raiz até à solução</li>
<li>
 - Factor de ramificação média - o número médio de ramos gerados por cada nó</li>
</ul>
<h3 id="a

### Algoritmos- de- procura">Algoritmos de procura</h3>
<p><img src="
![enter image description here](https://kevhuang.com/content/images/2015/06/tree-traversal.gif" alt="enter image description here"></p>
<h4 id="breadth-first-search">)

#### Breadth-first Search</h4>
<p>
Algoritmo de procura em <strong>largura</strong>__largura__, completa a exploração de todos os nós existentes num nível antes de passar para os seus filhos (nível seguinte).</p>
<h4 id="depth-first-search">

#### Depth-first Search</h4>
<p>
Algoritmo de procura em <strong>__profundidade</strong>__, explora sempre o nó aberto mais à esquerda e só depois de esgotar o caminho mais à esquerda volta os níveis necessários atrás até encontrar o nó mais à esquerda que não seja o que já foi esgotado.</p>
<h4 id="a---informed-search">

#### A* - informed search</h4>
<p>
O algoritmo A* é um algoritmo de procura <strong>__informada</strong>__, que faz uso de uma dada função heurística para atribuir um valor a cada nó que é gerado e opta por explorar sempre o nó de menor valor.</p>
<h3 id="exemplo-do-programa">Exemplo do programa</h3>
<p><img src="

### Exemplo do programa

![enter image description here](https://lh3.googleusercontent.com/WA8dXJ2VbAbgNj-E5bW2VmkCqXfuD2kzmXGgm4TGBFbJcadXxj929xg01ORo_We3byldsrgxpbw" alt=")
![enter image description here"><br>
<img src="](https://lh3.googleusercontent.com/7qpoLOle51l0yrRLIpBgpmIWxGQXgiZC-9SBmEV36WQZF7SYAMFDnNJbbGqBKlzm61sag0agjBA" alt="enter image description here"></p>)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzMzODI3NTI4LC00Mjc5NjM3MDJdfQ==
-->