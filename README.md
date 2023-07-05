# hemorrhage_detection_resnet50

## Motivação/Objetivo
O objetivo do trabalho é obter um modelo de aprendizado de máquina capaz de predizer, a partir de tomografias computadorizadas do cérebro de uma pessoa, se há ou não a condição hemorragia intracraniana.


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

   
3. Conversão dos arquivos DICOM em PNG

  Ap


### Link para a versão disponibilizada do dataset.
https://www.kaggle.com/competitions/rsna-intracranial-hemorrhage-detection/data

## Modelo de aprendizado de máquina

### Formalização matemática.

### Método de validação.

### Medidas de desempenho.


## Avaliação

### Amostras usadas para treinamento, validação e teste.

### Medidas de desempenho.


## Conclusão
