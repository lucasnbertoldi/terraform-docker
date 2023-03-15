# Terraform + Docker
Contém um modelo de estrutura de arquivos e scripts para executar o Terraform em um container. 

*Muito útil para desenvolvedores que **não querem instalar o Terraform** no computador ou precisam **testar versões** específicas facilmente.*

## Estrutura de pastas


**/main** - Arquivos da estrutura principal.

**/modules** - Módulos locais.

> Cada novo módulo deve ser inserido numa pasta dentro de modules.

## Executando o terraform

### Linux + Makefile

Execute o comando equivalente na pasta do projeto.

**terraform -v**

    make v

**terraform init**

    make i

**terraform plan**

    make p

**terraform apply**

    make a
*Não haverá a etapa de confirmação neste comando*

**terraform destroy**

    make d

---

#### Variáveis opcionais:

**module** - Executar o Terraform para algum módulo presente na pasta modules.

    make i module="module_1"
*Executa o terraform na pasta modules/module_1.*

---

**exec_user_code** e **exec_user_group** - Executa o Terraform com o código de algum grupo ou usuário específico.

    make i exec_user_code="1000" exec_group_code="1000"

### Windows e outros

**Crie um arquivo chamado .env** na pasta raiz e sempre edite a váriavel FOLDER para a pasta que quiser executar e EXEC_USER e EXEC_GROUP para os códigos do usuário e grupo respectivamente:

    FOLDER=main
    EXEC_USER=1000
    EXEC_GROUP=1000

Depois disso, execute o comando equivalente na pasta do projeto.

**terraform -v**

    docker-compose up terraform-version

**terraform init**

    docker-compose up terraform-init

**terraform plan**

    docker-compose up terraform-plan

**terraform apply**

    docker-compose up terraform-apply
*Não haverá a etapa de confirmação neste comando*

**terraform destroy**

    docker-compose up terraform-destroy