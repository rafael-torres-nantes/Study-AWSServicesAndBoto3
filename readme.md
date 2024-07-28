#  ☁️ Study Boto3 e Serviços da AWS

Bem-vindo ao repositório **Masterização de Habilidades com Boto3 e Serviços da AWS**! Este repositório é dedicado ao aprimoramento das habilidades no uso da biblioteca **boto3** para interagir com vários serviços da AWS. Através deste repositório, você aprenderá a utilizar serviços como **AWS Bedrock**, **DynamoDB**, **CloudWatch Logs**, **Polly**, **Rekognition**, **S3** e **Transcribe**.

📌 **Navegação**

- [📝 Visão Geral](#visão-geral)
- [🔧 Configuração e Testes](#configuração-e-testes)


## 📝 Visão Geral

Este repositório fornece um espaço para explorar e masterizar habilidades no uso de **boto3** com diversos serviços da AWS. O objetivo é familiarizar-se com a interação e a configuração desses serviços usando Python e boto3. 

Os principais serviços abordados incluem:

- **AWS Bedrock:** Serviço para criar e gerenciar modelos de machine learning.
- **DynamoDB:** Banco de dados NoSQL gerenciado e de alta performance.
- **CloudWatch Logs:** Serviço para monitorar, armazenar e acessar logs de aplicativos e infraestrutura.
- **Polly:** Serviço de síntese de voz para converter texto em fala.
- **Rekognition:** Serviço de análise de imagem e vídeo.
- **S3:** Serviço de armazenamento de objetos.
- **Transcribe:** Serviço de transcrição automática de áudio para texto.

## 🔧 Configuração e Testes

**Configuração:**

Certifique-se de que você tenha as credenciais da AWS configuradas corretamente no seu ambiente. Utilize o arquivo de configuração YAML abaixo para definir variáveis e permissões necessárias:

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
            - polly:SynthesizeSpeech
          Resource: "*" # Permissões para o serviço Polly
        - Effect: Allow
          Action:
            - logs:DescribeLogStreams
            - logs:CreateLogStream
            - logs:PutLogEvents
            - logs:CreateLogGroup
          Resource: arn:aws:logs:us-east-1:767398055833:log-group:rekognition-logs:log-stream:*
```


