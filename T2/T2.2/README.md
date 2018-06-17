# T2.2 - Clusteriza��o

## Enunciado/Tema:

Usando um data set dos 980 reposit�rios de GitHub com mais n�meros de estrelas at� junho de 2017 (em https://data.world/chasewillden/top-starred-open-source-projects-on-github), responder as diversas perguntas.

## Objetivo geral do trabalho:

Fazer an�lises para tirar algumas informa��es sobre os reposit�rios de GitHub com mais estrelas de usu�rios (pelo menos at� 6/24/2017) e procurar dar uma representa��o visual ao que foi achado.

## Data set utilizado:

https://data.world/chasewillden/top-starred-open-source-projects-on-github

Arquivo CSV 980 x 8 que possui de atributos:
- username (object)
- repository_name (object)
- description (object)
- last_update_date (date)
- language (object)
- number_of_stars (object)
- tags (object)
- url (object)

## Perguntas que planejamos responder:

1 - Quais s�o os 10 reposit�rios com mais estrelas?
2 - Quem s�o os donos do top 10 acima?
3 - Existem usu�rios com mais de um reposit�rio diferente listado no data set? Quais? Quantas vezes?
4 - Para cada usu�rio dono que aparece mais de uma vez, como � sua distribui��o de estrelas?
5 - Qual a m�dia do total de usu�rios listados por estrelas?
6 - Quais/quantas linguagens de programa��o temos no data set?
7 - Quais as linguagens do top 10 reposit�rios?
8 - Quais as top 10 lingagens do data set?
9 - Dos usu�rios que aparecem mais de uma vez, quantos possuem reposit�rios de linguagens diferentes (ex.: um reposit�rio em C, outro em Lua)?
10 - Quais os termos mais frequentes usados nas descri��es/tags?
11 - Crie gr�ficos do valor da m�trica silhouette para as clusteriza��es do dataset.
	Ideia: clusters entre usu�rios com mais de um reposit�rio (linguagens, quantidade de estrelas, tempo da �ltima atualiza��o at� a data de extra��o dos dados em 6/24/2017).

## Algoritmos/modelos que pretendemos utilizar:

- KMeans para determinar os clusters
- silhouette_samples e silhouette_score para calcular os clusters
- matplotlib.pyplot para gr�ficos
- wordcloud para mostrar frequ�ncia de palavras