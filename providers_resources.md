# Providers and Resoruces

<img width="415" height="470" alt="image" src="https://github.com/user-attachments/assets/3b0cbb5c-8297-406d-a2f6-28f43765fefe" />

## Providers
- `Providers` are plugins that let Terraform talk to different platforms, APIs, or services. In other way `Provider` is a plugin that helps to terraform to understand where to create specific infrastructure.
- `Providers` are Terraform plugins for cloud/services.
- These are like a bridge between Terraform and the actual infrastructure you’re managing.
- A provider knows how to manage resources for a specific service.
- Each provider exposes `resources` (things you can create) and `data sources` (things you can read).
- They define what resources you can manage.
- You configure them in provider blocks.
- You can use multiple providers in the same project.

- There are different types of providers
  - `Official` Providers
  - `Partner` Providers
  - `Community` Providers

```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = "us-east-1"
}
```

- `required_providers` → Tells Terraform which provider and version to use.
- `provider` "aws" → Configures that provider (like setting AWS region).

- We can use multiple providers as well.
```hcl
provider "aws" {
  region = "us-east-1"
}

provider "aws" {
  alias  = "west"
  region = "us-west-2"
}

resource "aws_instance" "east_server" {
  ami           = "ami-123456"
  instance_type = "t2.micro"
}

resource "aws_instance" "west_server" {
  provider      = aws.west   # <-- use aliased provider
  ami           = "ami-654321"
  instance_type = "t2.micro"
}
```

- Provider’s Resource
```hcl
resource "aws_s3_bucket" "example" {
  bucket = "my-example-bucket-123"
  acl    = "private"
}
```

```hcl
provider "aws" {
  region = "us-east-1"
}

provider "aws" {
  alias  = "west"
  region = "us-west-2"
}

resource "aws_instance" "east_server" {
  ami           = "ami-123456"
  instance_type = "t2.micro"
}

resource "aws_instance" "west_server" {
  provider      = aws.west   # <-- use aliased provider
  ami           = "ami-654321"
  instance_type = "t2.micro"
}
```
<br />

### Versions and Constraints
![Image](https://res.cloudinary.com/djgwvmcdl/image/upload/v1765723645/108fb5e4-a8ac-4d15-8b40-9d5b28b6d1f9.png)
