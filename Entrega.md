# T2: Programação Paralela Multithread 

## Parte I: Questões Pthreads
Especificações do computador utilizado -> Memória RAM: 8Gb, Processador: Ryzen 5 1400 3.2 Ghz 4 núcleos e 8 threads.

**1. Explique como se encontram implementadas as 4 etapas de projeto: particionamento, comunicação, aglomeração, mapeamento (use trechos de código para ilustrar a explicação).**

<h4>Particionamento</h4>

Abaixo é descrita a implementação da etapa de particionamento.

No trecho de código abaixo é especificada uma estrutura que é usada de forma global, ou seja, acessada por todas as threads que serão executadas. Essa estrutura é essencial para que os dados estejam acessíveis e para que seja feita a divisão e distribuição do vetor entre as threads.

<p align="center">
  <img src="https://github.com/elc139/t2-ggpereira/blob/master/img/questao1/particionamento_1.png">
 </p>
 
A função mostrada na figura a seguir implementa as operações que podem ser realizadas de forma paralela, assim cada thread acessa  porções de tamanho igual do vetor, produz um resultado parcial, calcula e armazena as somas parciais. A partir dessas somas ao final da execução das threads, temos o resultado.
 
<p align="center">
  <img src="https://github.com/elc139/t2-ggpereira/blob/master/img/questao1/particionamento_2.png"> 
 </p>

<h4>Comunicação</h4>

Na etapa de comunicação os dados necessários para a multiplicação que estão armazenados no vetor a e b são acessados, e o resultado é armazenado para obter o resultado parcial como mostra o código abaixo.

<p align="center">
  <img src="https://github.com/elc139/t2-ggpereira/blob/master/img/questao1/comunicacao_1.png">
</p>
 
<h4>Aglomeração</h4>

Na figura abaixo, o resultado da soma das multiplicações realizadas por cada thread é somado produzindo somas parciais até chegar ao resultado final.

<p align="center">
  <img src="https://github.com/elc139/t2-ggpereira/blob/master/img/questao1/aglomeracao_1.png"> 
 </p>

<h4>Mapeamento</h4>

Distribui as tarefas para as n threads, passando o índice(i) que é usado como offset para distribuir a carga. 

<p align="center">
  <img src="https://github.com/elc139/t2-ggpereira/blob/master/img/questao1/mapeamento_1.png"> 
 </p>

**2. Considerando o tempo (em microssegundos) mostrado na saída do programa, qual foi a aceleração (speedup) com o uso de threads?**

O Speedup foi de 1,95.

**3. A aceleração  se sustenta para outros tamanhos de vetores, números de threads e repetições? Para responder a essa questão, você terá que realizar diversas execuções, variando o tamanho do problema (tamanho dos vetores e número de repetições) e o número de threads (1, 2, 4, 8..., dependendo do número de núcleos). Cada caso deve ser executado várias vezes, para depois calcular-se um tempo de processamento médio para cada caso. Atenção aos fatores que podem interferir na confiabilidade da medição: uso compartilhado do computador, tempos muito pequenos, etc.**

As tabelas abaixo mostram que há pouca variação no valor do speedup para os tamanhos de vetores e repetições e na situação em que se aumenta o número de threads há um aumento proporcional do speedup.

<p align="center">
  <img src="https://github.com/elc139/t2-ggpereira/blob/master/img/questao3/tabela1_threads.PNG"> 
</p>

<p align="center">
  <img src="https://github.com/elc139/t2-ggpereira/blob/master/img/questao3/tabela2_threads.PNG">
</p>

<p align="center">
  <img src="https://github.com/elc139/t2-ggpereira/blob/master/img/questao3/tabela3_threads.PNG">
</p>

<p align="center">
  <img src="https://github.com/elc139/t2-ggpereira/blob/master/img/questao3/tabela4_threads.PNG">
</p>
