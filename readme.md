# ☁️ Masterização de Habilidades com Boto3 e Serviços da AWS

Bem-vindo ao repositório **Masterização de Habilidades com Boto3 e Serviços da AWS**! Este repositório é dedicado ao aprimoramento das habilidades no uso da biblioteca **boto3** para interagir com diversos serviços da AWS. Aqui, você encontrará recursos e exemplos para trabalhar com serviços como **AWS Bedrock**, **DynamoDB**, **CloudWatch Logs**, **Polly**, **Rekognition**, **S3** e **Transcribe**.

## 📌 Navegação

- [📝 Sobre o Projeto](#sobre-o-projeto)
- [📦 Instalação e Configuração](#instalação-e-configuração)
- [🔗 Conectar e Interagir com Serviços](#conectar-e-interagir-com-serviços)
- [📁 Estrutura do Repositório](#estrutura-do-repositório)
- [🔧 Configuração e Testes](#configuração-e-testes)

## 📝 Sobre o Projeto

O boto3 é a biblioteca oficial da AWS para Python, projetada para facilitar a interação com os serviços da AWS. Ele permite que você execute operações sobre recursos da AWS de forma programática, usando APIs específicas para cada serviço.

### Serviços Abordados

- **AWS Bedrock:** Criação e gerenciamento de modelos de machine learning.
- **DynamoDB:** Banco de dados NoSQL gerenciado e de alta performance.
- **CloudWatch Logs:** Monitoramento, armazenamento e acesso a logs de aplicativos e infraestrutura.
- **Polly:** Síntese de voz para converter texto em fala.
- **Rekognition:** Análise de imagens e vídeos.
- **S3:** Armazenamento de objetos.
- **Transcribe:** Transcrição automática de áudio para texto.

## 📦 Instalação e Configuração

### Instalação

Para instalar o boto3, execute o seguinte comando:

```bash
pip install boto3
```

### Configuração das Credenciais

As credenciais da AWS podem ser configuradas das seguintes maneiras:

- **Arquivo de Configuração:** Em `~/.aws/credentials` e `~/.aws/config`.
- **Variáveis de Ambiente:**
  - `AWS_ACCESS_KEY_ID`
  - `AWS_SECRET_ACCESS_KEY`
  - `AWS_SESSION_TOKEN`
- **AWS CLI:** Use o comando `aws configure` para configurar as credenciais e a região.

## 🔗 Conectar e Interagir com Serviços

Para interagir com os serviços da AWS usando boto3, siga estes passos:

### Criar um Cliente ou Recurso

```python
import boto3
client = boto3.client('service_name')  # Substitua 'service_name' pelo nome do serviço desejado
```

- **Cliente:** Interface de baixo nível para o serviço.
- **Recurso:** Interface de alto nível, orientada a objetos.

### Executar Operações

Para executar operações, utilize os métodos do cliente ou recurso:

```python
response = client.operation_name(Parameters)  # Substitua 'operation_name' e 'Parameters' conforme necessário
```

## 📁 Estrutura do Repositório

O repositório está organizado da seguinte forma:

1. **AWS Services:** Aplicações dos serviços usando uma estrutura orientada a objetos.
2. **Udemy - Master AWS with Python And Boto3:** Conteúdos das videoaulas da Udemy.

## 🔧 Configuração e Testes

### Configuração

Certifique-se de que as credenciais da AWS estejam configuradas corretamente em seu ambiente. Utilize o arquivo YAML abaixo para definir variáveis e permissões necessárias:

```yml
# Configuração do provedor AWS
provider:
  name: aws
  runtime: python3.10
  region: us-east-1
  environment:
    BUCKET_NAME: appsprint10  # Nome do bucket S3 
    DYNAMODB_TABLE_NAME: appsprint10db  # Nome da tabela DynamoDB
    TELEGRAM_TOKEN: 7208935989:AAE_44aNkDSbsHUSt3os0PH6PoIvQ5leGVQ # Token do Bot do Telegram
    LEX_BOT_ID: YXNYINYDS0  # ID do bot Lex V2
    LEX_BOT_ALIAS_ID: LOEIYAQGWP  # ID do alias do bot Lex V2
  iam:
    role: 
      statements:
        - Effect: Allow
          Action:
            - lex:PostText
          Resource: arn:aws:lexv2:us-east-1:851725456827:NatalDosPequenosChatbot/YXNYINYDS0/3
        - Effect: Allow
          Action:
            - s3:PutObject
            - s3:GetObject
            - s3:CreateBucket
            - s3:HeadBucket
          Resource: arn:aws:s3:::appsprint10/*  # Permissões para o bucket S3
        - Effect: Allow
          Action:
            - polly:SynthesizeSpeech
          Resource: "*"  # Permissão para o serviço Polly
        - Effect: Allow
          Action:
            - bedrock:InvokeModel
          Resource: "*"
        - Effect: Allow
          Action:
            - dynamodb:DescribeTable
            - dynamodb:Query
            - dynamodb:Scan
            - dynamodb:GetItem
            - dynamodb:PutItem
            - dynamodb:UpdateItem
            - dynamodb:DeleteItem
            - dynamodb:ListTables
          Resource: "*"  # Permissões para o DynamoDB
        - Effect: Allow
          Action:
            - rekognition:DetectLabels
            - rekognition:DetectText
            - rekognition:DetectImageProperties
          Resource: "*"  # Permissões para o serviço Rekognition
        - Effect: Allow
          Action:
            - transcribe:StartTranscriptionJob
            - transcribe:GetTranscriptionJob
            - transcribe:ListTranscriptionJobs
            - transcribe:DeleteTranscriptionJob
          Resource: "*"  # Permissões para o serviço Transcribe
        - Effect: Allow
          Action:
            - logs:DescribeLogStreams
            - logs:CreateLogStream
            - logs:PutLogEvents
            - logs:CreateLogGroup
          Resource: arn:aws:logs:us-east-1:767398055833:log-group:rekognition-logs:log-stream:*
```