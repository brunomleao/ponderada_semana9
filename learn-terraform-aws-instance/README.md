
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
**Local para Print 1: Saída do comando `terraform init`**

---

### 3. Validar o Código

Formate e valide a configuração para garantir que está correta:
```bash
terraform fmt
terraform validate
```
**Local para Print 2: Saída do comando `terraform validate`**

---

### 4. Criar a Infraestrutura

Execute o comando `terraform apply` para provisionar a instância EC2:
```bash
terraform apply
```
Confirme a execução digitando `yes` quando solicitado.

**Local para Print 3: Saída do comando `terraform apply` (incluindo o ID da instância)**

---

### 5. Verificar os Recursos

Verifique os recursos provisionados no AWS Console ou utilize o comando:
```bash
terraform show
```
**Local para Print 4: Saída do comando `terraform show`**

---

## Recursos Provisionados

Os seguintes recursos foram provisionados na AWS:

- **Instância EC2**:
  - Tipo: `t2.micro`
  - AMI: `ami-830c94e3`
  - Região: `us-west-2`
  - Tags: `Name = ExampleAppServerInstance`

**Local para Print 5: Print do Console AWS mostrando a instância criada**

---

## Limpar os Recursos

Para destruir os recursos criados, execute:
```bash
terraform destroy
```
Confirme digitando `yes`.

**Local para Print 6: Saída do comando `terraform destroy`**

---

## Estrutura do Repositório

```
|-- main.tf          # Código principal do Terraform
|-- README.md        # Documentação do projeto
```

---

## Conclusão

Este projeto demonstra como utilizar o Terraform para provisionar uma infraestrutura básica na AWS. É uma base para expandir com recursos adicionais, como redes, bancos de dados e armazenamento.

---

## Prints a Serem Adicionados

Sinalize os seguintes prints:
1. Saída do `terraform init`
2. Validação com `terraform validate`
3. Aplicação com `terraform apply`
4. Resultado do `terraform show`
5. Print do AWS Console mostrando a instância.
6. Saída do `terraform destroy`
