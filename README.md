# acppred

By Gabriela Luz

Uma ferramenta para a predição de peptídeos anticâncer

##Introdução

Essa ferramenta é destinada a identificação e predição de peptídeos anticâncer baseado em dados obtidos na plataforma AntiCP 2.0. A partir destes dados, o programa recebe duas listas, uma contendo os peptídeos anticâncer e outra os que não possuem atividade anticâncer, desta forma, treinamos o programa a identificar a semelhança dos peptídeos originados da base de dados com o peptídeo que o usuário inserir na ferramenta, e assim, mostrar o relatório classificatório após a avaliação. Para isso, se utiliza um estimador da biblioteca scikit learn para indicar o potencial anticâncer. 

##Input

A sequência do peptídeo que será analisado.
Exemplo: CGESCVWIPCVTSIFNCKCKENKVCYHDKIP

##Output

A predição da atividade anticâncer do peptideo num intervalo de 0 a 1.
Exemplo: 0.88

## Setup

```
$ make setup
```

##Funções 

###__init__(self, estimator, positive_peptides, negative_peptides): 
Essa classe define e treina um estimador para a predição de peptídeos anticâncer.
Args: 
  - estimator: um estimador do scikit-learn
  - positive_peptides: um arquivo contendo peptídeos anticâncer
  - negative_peptides: um arquivo contendo peptídeos não-anticâncer
  
###transform(self, X):
Essa função tranforma uma sequência de proteína em um percentual de aminoácidos
Args: 
  - X: uma lista de sequências de proteínas 
    
###train(self):
Essa função treina um modelo de predição para peptídeos anticâncer.

###predict(self, sequence):
Essa função prediz a atividade anticâncer para um dado peptídeo.
Args:
  - sequence: uma sequência de peptídeo que será analisada
  
###Save(self,filename):
Essa função salva o modelo em um arquivo
Args:
  - filename: caminho para o arquivo contendo o modelo treinado
  
###load(filename):
Essa função carrega o arquivo contendo o modelo treinado
Args:
  - filename: caminho para o arquivo contendo o modelo treinado

##Argumentos

'--positive-peptides', 
  default = 'data/raw/positive.txt',
  help='a file containing anticancer peptides'

'--negative-peptides',
  default = 'data/raw/negative.txt',
  help='a file containing non-anticancer peptides'
  
'--output',
  help='path to the output trained model',
  required=True
  
'--show-report',
  help='shows the classification report after training',
  action='store_true'
