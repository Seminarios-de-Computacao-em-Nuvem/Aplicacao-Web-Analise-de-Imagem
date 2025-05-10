# Seminário


Requisito	Como será atendido
2 serviços de computação	*EC2 + ECS (Fargate)*
2 serviços de banco de dados	RDS (MySQL/PostgreSQL) + DynamoDB
VPC customizada	Criar sua própria VPC com subnets públicas e privadas
Escalável	Auto Scaling + Fargate + ELB

 Requisitos eletivos:
Serviço eletivo	Como será usado
- S3	Armazenar imagens e arquivos estáticos
- Load Balancer e Auto Scaling	Balancear tráfego entre containers ou EC2
- Fargate	Executar containers Docker serverless
- API Gateway	Expõe sua API de forma gerenciável
- IA (Amazon Rekognition)	Ex: análise de imagens enviadas no S3

##  Visão Geral do Projeto
### Aplicação Web de análise de imagem:

- Frontend (React/Angular hospedado no S3)

- Backend em container (Docker) rodando no ECS com Fargate

- API exposta pelo API Gateway

- Banco de dados relacional no RDS

- Banco NoSQL no DynamoDB para cache/usuários

- Armazenamento de imagens no S3

- Quando imagem é enviada, uma função (opcional: Lambda) aciona o Amazon Rekognition para detectar faces ou objetos

Logs no CloudWatch

Toda rede em uma VPC customizada

##  Arquitetura (texto descritivo)
### Usuário acessa o frontend via CloudFront ou diretamente no S3

- O frontend envia requisições para o API Gateway

- O API Gateway redireciona para o backend rodando no ECS com Fargate

- O backend interage com:

- RDS para dados relacionais (produtos, perfis etc.)

- DynamoDB para dados rápidos ou históricos

- S3 para salvar imagens

- Amazon Rekognition para analisar imagens

- O Load Balancer distribui o tráfego entre containers

- A Auto Scaling cria mais containers conforme a demanda

- Logs e métricas monitorados pelo CloudWatch


![Alt text](image-1.png)
