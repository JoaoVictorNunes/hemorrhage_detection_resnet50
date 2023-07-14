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

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/e9cbe02f-6806-4abe-8bd3-bfa666068059)


### Método de validação.

Para a validação do modelo, foram separados 20% dos dados de treino.

### Medidas de desempenho.

As medidas de desempenhos utilizadas, em ordem decrescente de importância, foram:
1. Sensibilidade (Recall)
2. Especificidade (Specificity) 
3. Acurácia (Accuracy)

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

Loss:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/ec6321c7-2aa3-4045-99bd-c49da8df14f1)

Recall:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/feb794f6-4c7f-4395-9210-468d853d316d)

Specificity:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/3ded60a8-002d-4e14-aa79-7ea6962cbced)

Accuracy:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/85229f5b-fe96-451b-8081-be72a104c687)

Gráficos para a rodada 2:

Loss:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/1f40c6a3-c622-460e-894c-30dd203e8b8f)

Recall:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/692bab45-da3f-4e3c-b072-aaeb01db4ee1)

Specificity:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/d914d288-74c0-40ab-bb42-7947f7f9fd20)

Accuracy:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/f71645d6-87bb-468a-8518-07a895970ef0)


Com 150 épocas:

Loss:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/6234f855-3b44-479e-ba82-3c5d4a6aca66)


Recall:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/20602a4c-92ef-49c1-b6c1-abb7a7c18419)


Specificity:

![image](https://github.com/JoaoVictorNunes/hemorrhage_detection_resnet50/assets/83786352/76a7be22-9253-4e53-8180-bab1b048f49b)


A partir dos resultados obtidos, então, foi selecionado o modelo com lr = 0.0001.


## Conclusão

O modelo obtido desempenhou bem com relação à espcificidade, no entanto, sua sensibilidade foi baixa.
A acurácia, em torno de 54%, também foi aquém do esperado, visto que a classe majoritária representava 50% do dataset.
Desse modo, apesar de o desempenho do modelo nos datasets de validação e treinamento terem sido bastante satisfatórios, o comportamento não se repetiu para os dados de teste.


