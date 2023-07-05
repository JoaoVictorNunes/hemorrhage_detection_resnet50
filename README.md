# hemorrhage_detection_resnet50

## Motivação/Objetivo
O objetivo do trabalho é obter um modelo de aprendizado de máquina capaz de predizer, a partir de tomografias computadorizadas do cérebro de uma pessoa, se há ou não a condição hemorragia intracraniana.


## Descrição do Dataset

### Descrição dos dados
O dataset é composto por arquivos no formato DICOM. Não há informações acerca do paciente como sexo, idade, saúde, entre outros.
No total, há 700 mil imagens, com tamanho em torno de 480gb.


### Etapas de preparação dos dados ou pré-processamento.
A preparação dos dados consistiu em:
1. Balanceamento dos dados


   O dataset original é extremamente desbalanceado. Apenas 6% dos arquivos são referentes a imagens contendo hemorragia.
   Por tal motivo, foi aplicada a técnica de undersampling, selecionando todos os dados de imagens com hemorragia e o mesmo número de imagens sem hemorragias de forma aleatória.
   Nesse sentido, a etapa reduziu consideravelmente o tamnho do dataset original.

   
3. Conversão dos arquivos DICOM em PNG


### Link para a versão disponibilizada do dataset.


## Modelo de aprendizado de máquina

### Formalização matemática.

### Método de validação.

### Medidas de desempenho.


## Avaliação

### Amostras usadas para treinamento, validação e teste.

### Medidas de desempenho.


## Conclusão
