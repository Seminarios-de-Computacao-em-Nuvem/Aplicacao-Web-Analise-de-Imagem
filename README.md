# 🚀 Sobre o Projeto
Este projeto consiste na criação de uma arquitetura em nuvem escalável e resiliente utilizando Amazon Web Services (AWS), com foco na análise automatizada de imagens por meio do Amazon Rekognition.

A solução é composta por uma aplicação web, baseada em um frontend moderno, backend serverless e uma infraestrutura orientada a serviços gerenciados, visando:

## ✅ Alta disponibilidade.
## ✅ Escalabilidade automática.
## ✅ Desacoplamento de componentes.
## ✅ Minimização do gerenciamento de infraestrutura.

# 🏗️ Arquitetura e Fluxo
Usuário acessa o frontend hospedado no Amazon S3 via CloudFront (opcional).

O frontend envia requisições para o Amazon API Gateway.

O API Gateway redireciona as requisições para o backend containerizado rodando no Amazon ECS com Fargate.

O backend executa as seguintes ações:

Conecta-se ao Amazon RDS para persistência de dados relacionais.

Utiliza Amazon DynamoDB para armazenamento rápido e flexível de dados (cache, sessões, históricos).

Realiza operações de upload/download com o Amazon S3 para armazenar imagens.

Opcionalmente invoca o Amazon Rekognition para análise automatizada das imagens.

O Elastic Load Balancer (ELB) distribui o tráfego entre containers conforme a demanda.

O Auto Scaling ajusta automaticamente o número de containers, garantindo escalabilidade e resiliência.

Logs e métricas são enviados para o Amazon CloudWatch, possibilitando monitoramento contínuo.

# 🧰 Tecnologias e Serviços AWS
Categoria	Serviço AWS Utilizado
Computação	Amazon EC2, Amazon ECS (Fargate)
Bancos de Dados	Amazon RDS (MySQL/PostgreSQL), Amazon DynamoDB
Armazenamento	Amazon S3
Balanceamento e Escalabilidade	Elastic Load Balancer (ELB), Auto Scaling
API e Integração	Amazon API Gateway
Análise de Imagem	Amazon Rekognition
Rede e Segurança	Amazon VPC (customizada com subnets públicas e privadas)
Monitoramento	Amazon CloudWatch
Entrega de Conteúdo	AWS CloudFront (opcional)

# ✅ Requisitos Atendidos
Requisito	Implementação
2 serviços de computação	EC2 e ECS (Fargate) executando o backend de forma resiliente.
2 serviços de banco de dados	RDS para dados relacionais; DynamoDB para dados não-relacionais e de cache.
VPC customizada	VPC própria com subnets públicas (frontend, ELB) e privadas (banco, backend).
Escalabilidade	Auto Scaling + Fargate + ELB garantem ajuste automático conforme demanda.

# ⭐ Requisitos Eletivos
Serviço Eletivo	Utilização
Amazon S3	Armazenamento de imagens e arquivos estáticos.
Load Balancer + Auto Scaling	Balanceamento de tráfego entre containers e ajuste automático da capacidade.
AWS Fargate	Execução de containers Docker de forma serverless.
Amazon API Gateway	Exposição pública e gerenciável da API backend.
Amazon Rekognition	Análise automatizada de imagens enviadas (detecção de faces, objetos, textos).

# 🔐 Segurança e Boas Práticas
Utilização de IAM Roles com políticas de privilégios mínimos para cada serviço.

Subnets privadas para recursos críticos como RDS e ECS tasks.

Security Groups e Network ACLs configuradas para controle de tráfego.

Criptografia de dados em repouso no S3 e RDS.

Utilização de HTTPS no API Gateway para comunicação segura.

# 📊 Monitoramento e Observabilidade
Logs centralizados no Amazon CloudWatch Logs.

Alarmes e métricas configurados no CloudWatch Metrics para monitoramento de saúde e desempenho.

Possibilidade de configurar AWS X-Ray para rastreamento de requisições end-to-end.

# ⚙️ Implantação e Dependências
Pré-requisitos:
Conta AWS com permissões suficientes.

AWS CLI configurado.

Docker instalado.

Ferramentas de infraestrutura como código recomendadas: AWS CDK, Terraform ou CloudFormation.

Etapas:
Criar a VPC customizada com subnets públicas e privadas.

Configurar o S3 para hospedagem do frontend.

Deploy da aplicação backend no ECS com Fargate.

Configurar API Gateway para expor a API.

Criar e configurar RDS e DynamoDB.

Integrar com Amazon Rekognition.

Configurar Load Balancer e Auto Scaling.

Habilitar monitoramento com CloudWatch.

![image](https://github.com/user-attachments/assets/fd056267-afcc-40b7-b297-fe707b0b9064)
