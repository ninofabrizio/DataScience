# T1.2 - Modelos Preditivos

## Enunciado:
O objetivo deste trabalho � comparar diversos m�todos de classifica��o para a base de dados de qualidade de vinhos dispon�vel em https://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-red.csv.

Voc�s devem encontrar um bom modelo preditivo, variando:
* o n�mero e conjunto de features (atributos) utilizados
* o m�todo utilizado
* a configura��o do algoritmo correspondente (e.g.: n�mero k para nearest neighbors, profundidade para �rvore de decis�o)

Voc�s devem listar algumas m�tricas de qualidade, tais como: precision, recall, accuracy e f1_score, e utilizar accuracy como base para a avalia��o final, considerando a accuracy m�dia de 10 itera��es para cada configura��o.

Para assegurar que eu obterei os mesmos resultados de voc�s, voc�s devem estabelecer a semente para a gera��o dos n�meros aleat�rios (utilizados para separar os conjuntos de treinamento e teste, por exemplo), utilizando os seguintes comandos no in�cio do seu c�digo (podem utilizar uma outra semente):
```
import random
random.seed(1001001)
```