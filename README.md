# 🎥 Sistema de Reconhecimento Facial do Zero

Fala, pessoal! 👋

Este repositório contém a minha implementação para o projeto de criação de um sistema de reconhecimento facial, parte do bootcamp da DIO. O objetivo do desafio é construir um pipeline completo de Visão Computacional, unindo a detecção de rostos em uma imagem e a classificação de quem são essas pessoas.

## 🏭 O Cenário Escolhido

Para testar a rede, configurei as classes de predição focando em um elenco de peso do cinema. O sistema foi preparado para classificar as seguintes pessoas:
- Robert Pattinson
- Andy Serkis
- Colin Farrell
- Jeffrey Wright
- Scarlett Johansson
- Sebastian Stan

## 🛠️ Tecnologias e Arquitetura

Para fugir dos problemas de incompatibilidade de algoritmos estatísticos antigos (como o Haar Cascade), decidi modernizar o projeto dividindo-o em duas redes neurais distintas:

1. **Rede de Detecção (MTCNN):** Utilizei a Multi-task Cascaded Convolutional Networks (MTCNN). Diferente de métodos antigos, o MTCNN é uma rede neural super precisa que varre a imagem e retorna as *bounding boxes* (coordenadas) de múltiplas faces ao mesmo tempo, lidando muito bem com oclusões.
2. **Rede de Classificação (TensorFlow/Keras):** Construí uma Convolutional Neural Network (CNN) customizada (com camadas `Conv2D`, `MaxPooling2D` e `Dense`). Ela recebe o recorte exato do rosto identificado pelo MTCNN e passa por uma função de ativação `softmax` para determinar qual dos atores da nossa lista está na imagem.

## 🚀 Como testar o código

O projeto foi inteiramente desenvolvido em Python utilizando o **Google Colab**. 

1. Faça o upload do arquivo `.ipynb` deste repositório para o seu Colab.
2. O script conta com uma rotina de limpeza (`shutil`) e criação automática de pastas. Ele irá gerar imagens de ruído sintético apenas para permitir a compilação do modelo sem erros de falta de dados.
3. Para um treinamento real, basta substituir as imagens sintéticas na pasta `dataset_faces/treino/` por fotos reais (recortadas no rosto) de cada pessoa.
4. Ao final da execução, o script solicitará o upload de uma imagem de teste (uma foto em grupo) e plotará o resultado final com a detecção de todos os rostos encontrados.
