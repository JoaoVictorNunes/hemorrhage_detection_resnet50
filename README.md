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


### Método de validação.


### Medidas de desempenho.

As medidas de desempenhos utilizadas, em ordem decrescente de importância, foram:
1. Sensibilidade
2. Precisão
3. Acurácia

## Avaliação

### Seleção do Modelo

Devido ao grande tamanho do dataset e à capacidade computacional limitada, foi adotada uma estratégia para escolha do learning rate 

#### Ajuste fino do learning rate+


### Amostras usadas para treinamento, validação e teste.

### Medidas de desempenho.


## Conclusão
