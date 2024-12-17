# ponderada_semana9

Este repositório contém o passo a passo para provisionar uma **instância EC2** na AWS utilizando **Terraform**.

---

## Objetivo

O objetivo deste projeto é demonstrar como criar infraestrutura na nuvem utilizando **Infrastructure as Code (IaC)** com o Terraform.

---

## Pré-requisitos

Antes de iniciar, é necessário ter:

1. **Terraform CLI** (versão 1.2.0 ou superior) instalado.
2. **AWS CLI** configurado com suas credenciais:
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
3. Conta AWS com permissões para provisionar recursos.

---

## Passo a Passo

### 1. Configurar o Ambiente

1. Crie um diretório de trabalho:
   ```bash
   mkdir learn-terraform-aws-instance
   cd learn-terraform-aws-instance
   ```

2. Crie o arquivo **main.tf** e adicione o seguinte código:
   ```hcl
   terraform {
     required_providers {
       aws = {
         source  = "hashicorp/aws"
         version = "~> 4.16"
       }
     }

     required_version = ">= 1.2.0"
   }

   provider "aws" {
     region = "us-west-2" # Altere para sua região, se necessário
   }

   resource "aws_instance" "app_server" {
     ami           = "ami-830c94e3" # ID da AMI para a região us-west-2
     instance_type = "t2.micro"

     tags = {
       Name = "ExampleAppServerInstance"
     }
   }
   ```

3. Configure suas credenciais da AWS:
   ```bash
   export AWS_ACCESS_KEY_ID="sua_chave_de_acesso"
   export AWS_SECRET_ACCESS_KEY="sua_chave_secreta"
   ```

---

### 2. Inicializar o Terraform

Inicialize o diretório com o comando:
```bash
terraform init
```
<img width="886" alt="Captura de Tela 2024-12-17 às 11 08 55" src="https://github.com/user-attachments/assets/b171f572-a153-4ca9-a3ac-7de0b0a603ee" />

---

### 3. Criar a Infraestrutura

Execute o comando `terraform apply` para provisionar a instância EC2:
```bash
terraform apply
```
Confirme a execução digitando `yes` quando solicitado.
<img width="523" alt="Captura de Tela 2024-12-17 às 11 09 49" src="https://github.com/user-attachments/assets/1bbfd945-dc98-47da-861d-f71ec2447dd7" />

**Local para Print 3: Saída do comando `terraform apply` (incluindo o ID da instância)**

## Recursos Provisionados

Os seguintes recursos foram provisionados na AWS:

- **Instância EC2**:
  - Tipo: `t2.micro`
  - AMI: `ami-830c94e3`
  - Região: `us-west-2`
  - Tags: `Name = ExampleAppServerInstance`

**Local para Print 5: Print do Console AWS mostrando a instância criada**
<img width="1440" alt="Captura de Tela 2024-12-17 às 11 15 37" src="https://github.com/user-attachments/assets/c7159e2e-10cb-4280-9a50-ba8f49c0904a" />

---

## Estrutura do Repositório

```
|-- main.tf          # Código principal do Terraform
|-- README.md        # Documentação do projeto
```

---

## Conclusão

Este projeto demonstra como utilizar o Terraform para provisionar uma infraestrutura básica na AWS. É uma base para expandir com recursos adicionais, como redes, bancos de dados e armazenamento.
