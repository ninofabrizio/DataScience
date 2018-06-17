# T2.2 - Clusterização

## Enunciado/Tema:

Usando um data set dos 980 repositórios de GitHub com mais números de estrelas até junho de 2017 (em https://data.world/chasewillden/top-starred-open-source-projects-on-github), responder as diversas perguntas.

## Objetivo geral do trabalho:

Fazer análises para tirar algumas informações sobre os repositórios de GitHub com mais estrelas de usuários (pelo menos até 6/24/2017) e procurar dar uma representação visual ao que foi achado.

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

1 - Quais são os 10 repositórios com mais estrelas?<br/>
2 - Quem são os donos do top 10 acima?<br/>
3 - Existem usuários com mais de um repositório diferente listado no data set? Quais? Quantas vezes?<br/>
4 - Para cada usuário dono que aparece mais de uma vez, como é sua distribuição de estrelas?<br/>
5 - Qual a média do total de usuários listados por estrelas?<br/>
6 - Quais/quantas linguagens de programação temos no data set?<br/>
7 - Quais as linguagens do top 10 repositórios?<br/>
8 - Quais as top 10 lingagens do data set?<br/>
9 - Dos usuários que aparecem mais de uma vez, quantos possuem repositórios de linguagens diferentes (ex.: um repositório em C, outro em Lua)?<br/>
10 - Quais os termos mais frequentes usados nas descrições/tags?<br/>
11 - Crie gráficos do valor da métrica silhouette para as clusterizações do dataset.<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ideia: clusters entre usuários com mais de um repositório (linguagens, quantidade de estrelas, tempo da última atualização até a data de extração dos dados em 6/24/2017).

## Algoritmos/modelos que pretendemos utilizar:

- KMeans para determinar os clusters
- silhouette_samples e silhouette_score para calcular os clusters
- matplotlib.pyplot para gráficos
- wordcloud para mostrar frequência de palavras
