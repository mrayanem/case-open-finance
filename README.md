#  Solução AWS para Open Finance - Itaú Consignado

Arquitetura **serverless** para o compartilhamento seguro de dados cadastrais entre instituições financeiras, em conformidade com os requisitos do **Open Finance**.

---

##  Funcionalidades Principais

-  **Exposição de APIs** — API Gateway + AWS Lambda  
-  **Armazenamento Escalável** — Amazon DynamoDB + Aurora Serverless  
-  **Processamento Assíncrono** — Amazon SQS + EventBridge  
-  **Segurança Multicamadas** — WAF, Cognito, KMS, IAM  
-  **Observabilidade Completa** — CloudWatch, AWS X-Ray  

---

##  1. Introdução ao Problema

O desafio consiste em viabilizar o **compartilhamento seguro de dados cadastrais de clientes pessoa física** entre instituições financeiras parceiras, utilizando uma abordagem moderna baseada em:

- Microsserviços e arquitetura orientada a eventos  
- Escalabilidade automática com serverless  
- Alta observabilidade e rastreabilidade  
- Serviços nativos da AWS

###  Objetivo

- Garantir **segurança, eficiência e escalabilidade** no tráfego de dados sensíveis  
- Minimizar custos com **modelo pay-per-use**  
- Garantir **alta disponibilidade** e conformidade regulatória

---

##  2. Solução Implementada

###  Entrada de Dados (Inbound)

- **API Gateway + AWS Lambda**: Recebem requisições externas, validam e transformam os dados conforme regras de negócio.

###  Saída de Dados (Outbound)

- **AWS Lambda**: Consome dados armazenados (ex: no DynamoDB), realiza transformações necessárias e prepara os dados para envio.  
- **Amazon EventBridge / SQS**: Orquestra a entrega de eventos ou mensagens para destinos externos, garantindo resiliência e desacoplamento.  
- **API externa / HTTP**: Os dados são enviados para instituições parceiras ou outros consumidores por meio de APIs seguras.

###  Armazenamento

- **Amazon DynamoDB**: Banco NoSQL com alta performance e escalabilidade automática.  
- **Amazon Aurora Serverless** (opcional): Para casos onde dados relacionais sejam necessários.

###  Processamento e Orquestração

- **Amazon EventBridge**: Dispara eventos entre serviços com acoplamento mínimo.  
- **Amazon SQS**: Garante resiliência no tráfego assíncrono entre microsserviços.

###  Segurança

- **Amazon Cognito**: Gerencia autenticação e identidade dos usuários.  
- **AWS IAM + KMS + WAF + Shield**: Controle de acesso, criptografia, firewall e proteção contra ataques.

###  Observabilidade

- **Amazon CloudWatch + AWS X-Ray**: Monitoramento, métricas e rastreamento completo de requisições.

###  FinOps e Escalabilidade

- Adoção de arquitetura **serverless** reduz custos operacionais.  
- **Lambda e DynamoDB** escalam automaticamente com a demanda real.

###  Diagrama Resumo da Arquitetura

![case-openfinance drawio](https://github.com/user-attachments/assets/a276844b-2b5e-4e98-84b9-7936bb51270d)

---

##  3. Resultados Obtidos

A solução implementada oferece:

-  **Segurança e conformidade** com os padrões do Open Finance  
-  **Escalabilidade automática** e gerenciamento eficiente de carga  
-  **Resiliência**, com filas e eventos para evitar falhas entre sistemas  
-  **Redução de custos**, com cobrança sob demanda (serverless)  
-  **Observabilidade e auditoria** via logs, métricas e rastreamento

---

##  Conclusão

A arquitetura proposta utiliza o melhor do ecossistema AWS para criar uma solução moderna, segura, escalável e de fácil manutenção. Ideal para ambientes regulados, como o Open Finance, ela entrega valor com agilidade, confiabilidade e otimização de custos.

---
