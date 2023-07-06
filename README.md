# hemorrhage_detection_resnet50

## Motivação/Objetivo
O objetivo do trabalho é obter um modelo de aprendizado de máquina capaz de predizer, a partir de tomografias computadorizadas do cérebro de uma pessoa, se há ou não a condição hemorragia intracraniana.

### Limitação Computacional

## Descrição do Dataset

### Descrição dos dados
O dataset é composto por arquivos no formato DICOM. Não há informações acerca do paciente como sexo, idade, saúde, entre outros.
No total, há 753 mil imagens, com um tamanho total de 458.97 GB.

### Etapas de preparação dos dados ou pré-processamento.
A preparação dos dados consistiu em:
1. Balanceamento dos dados

   O dataset original é bastante desbalanceado. Apenas 14.42% dos arquivos são referentes a imagens contendo hemorragia.
   Por tal motivo, foi aplicada a técnica de undersampling, selecionando todos os dados de imagens com hemorragia e o mesmo número de imagens sem hemorragias de forma aleatória.
   Nesse sentido, a etapa reduziu consideravelmente o tamanho do dataset original, mas o dataset ainda se manteve com um tamnho bastante expressivo: 217 mil imagens.

2. Conversão dos arquivos DICOM em PNG

   Nesta etapa, as imagens em formato DICOM foram convertidas para PNG, com o objetivo de torná-las possíveis de serem processadas pelo modelo de Rede Neural selecionado.

3. Outros processamentos
   1. Os pixels das imagens foram normalizados
   2. Dimensões alteradas para 180 px por 180 px
   3. Não houve a aplicação de técnicas de data augmentation dada a limitação da capacidade computacional


### Link para a versão disponibilizada do dataset.
https://www.kaggle.com/competitions/rsna-intracranial-hemorrhage-detection/data

## Modelo de aprendizado de máquina
O modelo utilizado foi a Residual Neural Network, ou ResNet, com 50 camadas ocultas.

### Método de validação.

Para a validação do modelo, foram separados 20% dos dados de treino.

### Medidas de desempenho.

As medidas de desempenhos utilizadas, em ordem decrescente de importância, foram:
1. Sensibilidade
2. Precisão
3. Acurácia

Dada a natureza do problema, a ordem foi definida dessa maneira com o objetivo de minimizar o acontecimento de falsos negativos. 

## Avaliação

### Seleção do Melhor Modelo

A seleção do modelo foi realizada em duas etapas:
1. Treino, com 2.000 arquivos e 10 épocas, de 6 valores de learning rate: 0.01, 0.001, 0.0001, 0.00001 e 0.000001.
2. Após a seleção dos modelos que melhor desempenharam no passo 1, foi realizada uma nova rodada, mas dessas vez com 30 épocas.


Em seguida, após a seleção do learning rate otimizado, foi realizado o treinamento da rede neural com 20.000 imagens e 30 épocas.

### Amostras usadas para treinamento, validação e teste.

### Medidas de desempenho.


## Conclusão
