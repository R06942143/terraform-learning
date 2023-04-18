# terraform-learning
## Setup
---
### [Terraform](https://github.com/hashicorp/terraform)
1. Navigate to the Terraform [download page](https://developer.hashicorp.com/terraform/downloads)

2. Run the following command to verify terraform is installed.
```
terraform -v
```

### [Tflint](https://github.com/terraform-linters/tflint)
1. Use the following command to download the terraform
```
curl -s https://raw.githubusercontent.com/terraform-linters/tflint/master/install_linux.sh | bash
```
2. Run the following command to verify tflint is installed.
```
tflint
```

## Project Layout
---
    .
    ├── config                   # Terraform Backend configuration
    │   ├── staging.hcl          # The key-value pair of the terraform backend configuration
    │   ├── production.hcl       # If you want to be more secure, you should pass the value in CD.
    │   └── dev.hcl              # The key-value pair of the terraform backend configuration
    ├── env                      # The place to put tfvars
    │   ├── staging.tfvars       # The key-value pair of the terraform backend configuration
    │   ├── production.tfvars    # If you want to be more secure, you should pass the value in CD.
    │   └── dev.tfvars           # The key-value pair of the terraform backend configuration
    ├── tf                       # Source files (alternatively `lib` or `app`)
    │   ├── modules              # The tf files that will be imported
    │   └── application          # The place for you to implement your infra logic
    ├── backend.tf               # 
    ├── main.tf                  # The root file. Typically we will put the shared component here.(network, cluster, ip, vpc)
    ├── variables.tf             # Variables
    ├── version.tf               # Required terrform/plugin version
    ├── LICENSE
    └── README.md
## Usage
Initialize terraform with the envrionment variable
```
terraform init -backend-config=config/staging.hcl
```

Show what terraform will evaluate
```
terraform plan
```

Save the plan
```
terraform plan -out=sample-deployment
```

Automatically Format Terraform
```
terraform fmt
```