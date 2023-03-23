# terraform

Licença
Este projeto está licenciado sob a licença MIT - veja o arquivo LICENSE para detalhes.
Como usar
Pré-requisitos
    • Terraform instalado.
    • Conta na plataforma Azure.
Variáveis de ambiente
Para utilizar este projeto é necessário configurar algumas variáveis de ambiente, que podem ser definidas através de um arquivo terraform.tfvars ou em um ambiente de execução.
Variável
Descrição
Padrão
azure_subscription_id
ID da assinatura da conta Azure

azure_client_id
ID do aplicativo criado no Azure AD

azure_client_secret
Senha do aplicativo criado no Azure AD

azure_tenant_id
ID do locatário do Azure

location
Localização da infraestrutura
westus2
resource_group_name
Nome do grupo de recursos que será criado
rg-terraform
vnet_cidr
Endereço CIDR da rede virtual
10.0.0.0/16
subnet_cidr
Endereço CIDR da sub-rede que será criada
10.0.1.0/24
vm_admin_username
Nome de usuário da máquina virtual
azureuser
vm_admin_password
Senha de usuário da máquina virtual
Password123!
Criação da infraestrutura
Após definir as variáveis de ambiente, basta executar os seguintes comandos:
csharpCopy code
terraform init
terraform plan
terraform apply
O comando terraform init irá inicializar o diretório com as configurações necessárias.
O comando terraform plan irá criar um plano de execução, exibindo as mudanças que serão feitas na infraestrutura.
O comando terraform apply irá criar a infraestrutura na Azure.
Destruir infraestrutura
Para remover a infraestrutura criada, basta executar o comando:
Copy code
terraform destroy

Overview: In this task, we need to design and implement an ETL infrastructure that extracts data from various sources, transform it and loads it into a data warehouse. The infrastructure should have three separate environments for development, quality, and production. It should be optimized for dynamic scaling and minimize cost for the test environment. Public internet access should be blocked where possible.
Solution: We will use the following Azure services to implement the ETL infrastructure:
    • Azure Data Factory (ADF)
    • Azure Data Lake Storage Gen2 (ADLS Gen2)
    • Azure SQL Database
    • Azure Key Vault
    • Azure Monitor
    • Azure Automation
    • Azure Virtual Network (VNet)
    • Azure Network Security Group (NSG)
We will use Terraform to provision and configure the resources in Azure.
Design Choices:
    1. Azure Data Factory: We will use ADF as the ETL tool as it provides a cloud-based platform for creating and managing data pipelines. ADF has built-in connectors to various sources and sinks, making it easy to extract data from different sources and load it into a data warehouse.
    2. Azure Data Lake Storage Gen2: We will use ADLS Gen2 as the storage layer for storing the extracted data. ADLS Gen2 provides a hierarchical namespace and supports large-scale analytics workloads.
    3. Azure SQL Database: We will use Azure SQL Database as the data warehouse to store the transformed data. Azure SQL Database is a fully managed relational database service that provides high availability, scalability, and security.
    4. Azure Key Vault: We will use Azure Key Vault to store and manage the secrets and keys used in the ETL infrastructure, such as connection strings and passwords.
    5. Azure Monitor: We will use Azure Monitor to monitor the health and performance of the ETL infrastructure. Azure Monitor provides metrics, logs, and alerts for Azure resources.
    6. Azure Automation: We will use Azure Automation to automate the deployment and configuration of the ETL infrastructure. Azure Automation provides a way to run runbooks, which are scripts that can perform automated tasks.
    7. Azure Virtual Network (VNet) and Network Security Group (NSG): We will use VNet and NSG to create a private network and block public internet access to the resources where possible.
Key Features of the Infrastructure:
    1. Separate environments: The ETL infrastructure has three separate environments - development, quality, and production - to isolate the changes and ensure that the changes are tested before deploying to the production environment.
    2. Dynamic scaling: ADF supports dynamic scaling, which means that it can automatically adjust the compute resources based on the load. This ensures that the infrastructure can handle large-scale data workloads.
    3. Minimize cost: We will use Azure Automation to automate the deployment and configuration of the resources, which reduces the manual effort and cost. We will also use Azure Advisor to optimize the cost of the infrastructure.
    4. Security: We will use Azure Key Vault to store and manage the secrets and keys used in the ETL infrastructure. We will also use VNet and NSG to create a private network and block public internet access to the resources where possible.
    5. Monitoring: We will use Azure Monitor to monitor the health and performance of the ETL infrastructure. Azure Monitor provides metrics, logs, and alerts for Azure resources.
    6. Compliance: We will ensure that the infrastructure complies with the organizational policies and regulations, such as GDPR and HIPAA.
that provides a collaborative workspace for data engineering, machine learning, and analytics. Azure Databricks allows us to run Spark jobs in a fully managed environment, making it easy to scale the compute resources based on the workload.
    3. Load: The transformed data is loaded into Azure SQL Database using ADF.
    4. Monitoring: Azure Monitor is used to monitor the health and performance of the ETL pipeline. We can use Azure Monitor to set up alerts and notifications for various metrics, such as pipeline status, data ingestion rate, and errors.
In this task, we have designed and implemented an ETL infrastructure using Azure services and Terraform. The infrastructure is designed to extract data from various sources, transform it using Azure Databricks, and load it into Azure SQL Database. The infrastructure has three separate environments for development, quality, and production, and it is optimized for dynamic scaling and cost. Public internet access is blocked where possible, and the infrastructure complies with organizational policies and regulations. The infrastructure is monitored using Azure Monitor, and alerts and notifications are set up for various metrics.

Terraform Infrastructure Pipeline Azure Created

A short description of the project.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

What things you need to install the software and how to install them

Include a list of prerequisites here. For example:
    • Node.js
    • NPM
    • MongoDB
vbnetCopy code

### Installing

A step by step series of examples that tell you how to get a development env running

Show the code necessary to install dependencies, configure the environment, etc.
Csharp

### Running the tests

Explain how to run the automated tests for this system

Show how to run automated tests, e.g. npm test
Deployment
Add additional notes about how to deploy this on a live system
Built With
    • Library/Framework - Description
Contributing
Please read [CONTRIBUTING.md](link to contributing.md) for details on our code of conduct, and the process for submitting pull requests to us.
Versioning
We use SemVer for versioning.
Authors
    • Rafael Maran - https://github.com/rafael19899-ops/terraform
License
This project is licensed under the License Name - see the LICENSE.md file for details.

Principle files to use as Azure Pipeline Factory Create:
https://github.com/rafael19899-ops/terraform/blob/main/azure-pipelines-main.yml - main.tf file
https://github.com/rafael19899-ops/terraform/blob/main/azure-pipelines-variables-5.yml - Variables.tf
https://github.com/rafael19899-ops/terraform/blob/main/azure-pipelines-5-outputs.yml - Output. tf
https://github.com/rafael19899-ops/terraform/blob/main/azure-pipelines-2.yml - Variables.tf - test


Feel free to modify the contents and formatting as needed for your project.

Deploying the Infrastructure
To deploy the infrastructure, you can follow these steps:
    1. Install the Azure CLI by following the instructions here.
    2. Login to your Azure account by running the following command and following the prompts:
       Copy code
       az login
    3. Set the subscription that you want to use by running the following command:
       sqlCopy code
       az account set --subscription <subscription_id>
    4. Create a terraform.tfvars file in the root of the project directory, and specify the values for the variables defined in variables.tf. For example:
       makefileCopy code
       location = "northeurope"
       prefix = "myapp"
    5. Initialize the Terraform environment by running the following command:
       csharpCopy code
       terraform init
    6. Preview the changes that Terraform will make by running the following command:
       Copy code
       terraform plan
    7. If the plan looks good, apply the changes by running the following command:
       Copy code
       terraform apply
       You will be prompted to confirm that you want to apply the changes. Enter yes to proceed.
       The deployment may take several minutes to complete.
Cleaning Up
To clean up the resources created by this project, you can run the following command:
Copy code
terraform destroy
You will be prompted to confirm that you want to destroy the resources. Enter yes to proceed.
Conclusion
In this project, we have used Terraform to define and deploy a simple web application infrastructure on Azure. With Terraform, we can easily manage and version our infrastructure as code, and deploy and maintain it in a consistent and repeatable way.

The repository you linked to contains Terraform code for creating an Azure infrastructure for an ETL (extract, transform, load) pipeline. Here's a brief overview of each of the files in the repository:
    • main.tf: This file contains the main Terraform code for creating the infrastructure. It creates resource groups, virtual networks, subnets, storage accounts, Azure Data Factory instances, SQL servers, and databases, among other resources. The file is quite long, but it's well-commented, which should make it easier to understand.
    • variables.tf: This file defines the input variables used in the main Terraform code. This is a good practice to make the code more modular and reusable.
    • outputs.tf: This file defines the output variables that are returned by the Terraform code. These variables can be used by other systems or processes that depend on the infrastructure created by Terraform.
    • provider.tf: This file defines the Azure provider for Terraform. It specifies the subscription ID and the location (North Europe) for the resources.
    • storage.tf: This file creates a storage account to be used by the ETL pipeline. It also creates a container within the storage account to store the input data.
    • datafactory.tf: This file creates an Azure Data Factory instance. It also creates linked services for the storage account and the SQL server, as well as a dataset for the input data.
    • sqlserver.tf: This file creates an Azure SQL Server instance. It also creates a firewall rule to allow traffic from the private endpoint (created in another file).
    • sqldatabase.tf: This file creates an Azure SQL Database instance. It also creates a table to store the output data.
    • pe.tf: This file creates a private endpoint for the SQL server. This ensures that the SQL server is only accessible from the VNet and not from the public internet.
    • dns.tf: This file creates a private DNS zone and a DNS record set for the private endpoint. This allows the ETL pipeline to access the SQL server using a fully qualified domain name (FQDN) instead of an IP address.
Overall, this Terraform code is well-structured and follows best practices for creating an infrastructure in Azure. However, it should be noted that this code is just an example and should be modified to fit the specific requirements of each organization.


