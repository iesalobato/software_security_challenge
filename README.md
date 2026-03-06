# Projeto MVP para o Desafio TC5 - FIAP Software Security**

Um sistema inteligente que utiliza Visão Computacional (YOLOv8) para analisar diagramas de arquitetura de software, identificar componentes críticos e gerar automaticamente um relatório de Modelagem de Ameaças baseado na metodologia **STRIDE**.

---

## Sobre o Projeto

No desenvolvimento moderno de software, a segurança muitas vezes é deixada para o final. A modelagem de ameaças é crucial, mas exige tempo e especialistas. 
Este MVP resolve esse problema automatizando o processo: basta fazer o upload da imagem de um diagrama de arquitetura (ex: AWS, Azure, GCP), e a nossa Inteligência Artificial deteta os componentes e sugere vulnerabilidades e contramedidas instantaneamente.

## Funcionalidades

* **Deteção de Objetos via IA:** Treinamento de um modelo YOLOv8 customizado para reconhecer padrões de arquitetura em imagens.
* **Mapeamento de Classes:** O modelo foi treinado para identificar 6 categorias vitais:
  * `frontend` (Interfaces, Web Consoles, Apps)
  * `api_gateway` (Gestores de Tráfego e APIs)
  * `auth_service` (Cognito, IAM, Serviços de Identidade)
  * `app_service` (Lambdas, ECS, Microserviços)
  * `database` (S3, RDS, DynamoDB)
  * `messaging` (IoT Core, SQS, Filas)
* **Motor STRIDE Integrado:** Algoritmo em Python que cruza os componentes detetados com uma base de conhecimento de segurança para gerar um relatório estruturado.

---

## Tecnologias Utilizadas

* **Linguagem:** Python 3
* **Visão Computacional:** YOLOv8 (Ultralytics), OpenCV
* **Processamento de Dados:** Pandas, Matplotlib
* **Ambiente de Desenvolvimento:** Google Colab (Treinamento com GPU T4)
* **Anotação de Dataset:** Roboflow / MakeSense.ai

---

## Como Executar o Projeto

Como o modelo exige capacidade de processamento (GPU) para inferência rápida, todo o projeto foi estruturado num Notebook interativo.

1. Faça upload do notebook deste repositório para o Google Colab.
2. No menu superior, clique em **Ambiente de Execução** > **Executar Tudo**.
3. Vá até à secção **4. Inferência Dinâmica** e clique no botão `Upload` para enviar a imagem do seu diagrama.
4. O sistema irá exibir a imagem com as _bounding boxes_ (quadrados de deteção) desenhadas e, em seguida, imprimirá o Relatório STRIDE completo no ecrã.

---

## Metodologia de Treinamento

O modelo base utilizado foi o `yolov8n.pt` (Nano), otimizado para velocidade. O dataset foi construído manualmente e submetido a técnicas de anotação de _bounding boxes_.
* **Épocas (Epochs):** 500 (com Early Stopping)
* **Confiança de Inferência (Conf):** 0.05 (Ajustado para o MVP)

---

## 👥 Equipa

* **[Teu Nome / Nome do Grupo]** - Desenvolvimento de IA e Segurança de Software.
