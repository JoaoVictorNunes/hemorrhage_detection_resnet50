# hemorrhage_detection_resnet50

## Motivação/Objetivo
O objetivo do trabalho é obter um modelo de aprendizado de máquina capaz de predizer, a partir de tomografias computadorizadas do cérebro de uma pessoa, se há ou não a condição hemorragia intracraniana.

### Limitação Computacional

## Descrição do Dataset


### Descrição dos dados
O dataset é composto por arquivos no formato DICOM. Não há informações acerca dos pacientes como sexo, idade, saúde, entre outros.
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
   3. A ordem das imagens foram randomizadas.
   4. Não houve a aplicação de técnicas de data augmentation dada a limitação da capacidade computacional


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
1. Treino, com 2.000 arquivos e 10 épocas, de 5 valores de learning rate: 0.01, 0.001, 0.0001, 0.00001 e 0.000001.
2. Após a seleção dos modelos que melhor desempenharam no passo 1, foi realizada uma nova rodada, mas dessas vez com 30 épocas.

Após a primeira rodada, os valores de melhor desempenho foram: 0.01, 0.001 e 0.0001. Foram eliminados, portanto, as duas menores taxas de learning rate.

Como pode ser observado nos gráficos de recall, accuracy e precision, para os valores lr_4 e lr_5, não houve melhorias no treinamento com 10 épocas.
Além disso, como se esperava


Gráficos para a rodada 1:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/ec6321c7-2aa3-4045-99bd-c49da8df14f1)
![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/feb794f6-4c7f-4395-9210-468d853d316d)
![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/8e560e42-e765-4135-849b-3b141d1f8c31)
![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/85229f5b-fe96-451b-8081-be72a104c687)

Gráficos para a rodada 2:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/d1d4c36b-de8c-48ea-aab7-ecadec09e505)
![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/692bab45-da3f-4e3c-b072-aaeb01db4ee1)
![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/614b69a2-6a29-4e69-b340-1836ea97e07f)
![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/f71645d6-87bb-468a-8518-07a895970ef0)

Em seguida, após a seleção do learning rate otimizado, foi realizado o treinamento da rede neural com 20.000 imagens e 30 épocas.

### Amostras usadas para treinamento, validação e teste.

### Medidas de desempenho.


## Conclusão
