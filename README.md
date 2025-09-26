# PROJETO-AWS-AGENDA-INTELIGENTE
Santander Code Girls - 2025

Este projeto apresenta a arquitetura em AWS para um Micro SaaS de agendamento inteligente voltado para manicures.   A solução foi modelada em 3D no draw.io e contempla serviços da Amazon Web Services com foco em escalabilidade, segurança e custo acessível.

💅 Micro SaaS de Agendamento Inteligente para Manicure

<img width="1446" height="803" alt="image" src="https://github.com/user-attachments/assets/039418fd-5fcd-430e-abff-1af7bda135a4" />

---

🎯 Objetivo

Oferecer uma plataforma SaaS que permita:
- Manicures cadastrarem seus horários disponíveis.  
- Clientes agendarem horários de forma rápida e intuitiva.  
- Algoritmos inteligentes sugerirem o melhor horário, usando **AWS Lambda**.  

---

🏗️ Arquitetura da Solução

A arquitetura foi construída em **camadas**, seguindo boas práticas da AWS:

🔹 Camada Usuário
- **Clientes (Web/Mobile)** acessam o sistema por domínio próprio.

🔹 Camada DNS & Entrada
- **Amazon Route 53** → Gerencia o domínio (ex.: `meuagenda.com`).  
- **Application Load Balancer (ALB)** → Distribui o tráfego entre instâncias EC2 com SSL/TLS.

🔹 Camada Aplicação
- **Amazon EC2** → Hospeda a aplicação (frontend + backend).  
- **AWS Lambda** → Processa lógica inteligente de agendamento e recomendações.

🔹 Camada Dados
- **Amazon RDS (PostgreSQL/MySQL)** → Armazena cadastros, horários e agendamentos.  
- **Amazon S3** → Armazena imagens (portfólios, logos) e arquivos estáticos (CSS, JS).  
- **Amazon DynamoDB (opcional)** → Cache e sessões rápidas.

🔹 Camada Observabilidade & Segurança
- **Amazon CloudWatch** → Métricas de CPU, logs de aplicação, alarmes.  
- **AWS IAM** → Controle de acesso seguro para usuários e serviços.  
- **AWS CloudTrail** → Auditoria das ações na conta AWS.

---

🔄 Fluxo Resumido

1. Usuário acessa `(EXEMPLO DE DOMINIO - minhaagendamanicure.com`.  
2. **Route 53** direciona para o **ALB**.  
3. **ALB** envia a requisição para a aplicação hospedada em **EC2**.  
4. A aplicação consulta/grava dados no **RDS** e utiliza **S3** para arquivos estáticos.  
5. Funções inteligentes são executadas via **AWS Lambda**.  
6. Métricas e logs são coletados no **CloudWatch**.  
7. A segurança e auditoria são garantidas por **IAM** e **CloudTrail**.

--- 
📖 Como Abrir o Diagrama
Acesse draw.io (diagrams.net)
--- 
🛠️ Tecnologias AWS Utilizadas

Route 53
Application Load Balancer (ALB)
EC2
Lambda
RDS
S3
DynamoDB
CloudWatch
IAM
CloudTrail

--- 
💰 Custos Estimados (MVP - Micro SaaS)
Valores aproximados em USD/mês, considerando uso moderado e instâncias pequenas na região us-east-1:

| Serviço              | Configuração Básica                | Custo Estimado |
| -------------------- | ---------------------------------- | -------------- |
| **EC2**              | 1x t3.micro (24/7)                 | ~ $9           |
| **RDS**              | db.t3.micro (Single AZ)            | ~ $15          |
| **S3**               | 10 GB + 100k requisições           | ~ $1           |
| **Lambda**           | 1M execuções/mês (free tier cobre) | ~$0            |
| **ALB**              | 1 ALB ativo                        | ~ $18          |
| **Route 53**         | 1 domínio + 1 hosted zone          | ~ $1,5         |
| **CloudWatch**       | Logs + métricas básicos            | ~ $2           |
| **IAM / CloudTrail** | Incluídos no free tier             | $0             |

🔹 Total aproximado: ~ $45/mês

(varia conforme tráfego e uso real, podendo ser otimizado para < $30 com free tier nos primeiros 12 meses).

--- 
📌 Licença

Este projeto é apenas um estudo de caso educacional e não possui fins comerciais diretos.
Sinta-se livre para reutilizar a arquitetura em seus próprios projetos SaaS.
--- 
📂 Estrutura do Repositório

```bash
.
├── LICENSE
├── Projeto AWS - Agenda inteligente - SAAS.drawio  # Diagrama em 3D da arquitetura
├── README.md 


