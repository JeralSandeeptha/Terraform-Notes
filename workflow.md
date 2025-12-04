# Terraform Workflow (The Complete Guide)

Terraform follows a standard 4-step workflow:
  - `Write`
  - `Initialize`
  - `Plan`
  - `Apply`
  - `Detroy`

✅ 1. Write (Configuration)
We write .tf files using HCL (HashiCorp Configuration Language).

Typical files:
- `main.tf` – main resources
- `variables.tf` – variables
- `outputs.tf` – outputs
- `provider.tf` – provider configs

```bash
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "web" {
  ami           = "ami-12345"
  instance_type = "t2.micro"
}
```

<br />

✅ 2. Initialize

```bash
terraform init
```

What it does:
- Downloads provider plugins (AWS, GCP, Azure, etc.)
- Creates a .terraform directory
- Reads backend configuration (for state storage)

You run this whenever:
- You add/change a provider
- You clone a Terraform project
- You use modules

<br />

✅ 3. Plan
This is a preview of what Terraform will do. Nothing is deployed yet — this is just a dry run.

```bash
terraform plan
```

Terraform compares:
- Your current configuration (.tf files)
- Terraform state file (terraform.tfstate)
- Real infrastructure in cloud provider

Plan will show:
- What will be created
- What will be updated
- What will be deleted

```bash
+ aws_instance.web
    ami: "ami-1234"
    instance_type: "t2.micro"
```

<br />

✅ 4. Apply

Terraform will:
- Re-run the plan
- Ask for confirmation (unless -auto-approve)
- Provision/update/delete infrastructure

```bash
terraform apply
```

```bash
aws_instance.web: Creating...
aws_instance.web: Creation complete.
```

<br />

✅ 5. Destroy
Destroys all resources created by Terraform.

Use when:
- Deleting environments
- Cleaning cloud resources to avoid billing

```bash
terraform destroy
```

<br />

✅ Summary

```bash
     ┌──────────┐
     │  Write   │  (main.tf)
     └─────┬────┘
           ↓
     ┌──────────┐
     │   Init   │  (terraform init)
     └─────┬────┘
           ↓
     ┌──────────┐
     │   Plan   │  (terraform plan)
     └─────┬────┘
           ↓
     ┌──────────┐
     │  Apply   │  (terraform apply)
     └─────┬────┘
           ↓
     ┌──────────┐
     │ Destroy  │  (optional)
     └──────────┘
```
