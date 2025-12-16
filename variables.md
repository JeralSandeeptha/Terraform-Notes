## Variables
- Variables in Terraform are essential for parameterizing and sharing values within your Terraform configurations and modules
- They allow you to make your configurations more dynamic, reusable, and flexible

- There are 3 types of variables
    - `Locals` variables
    - `Input` variables
    - `Output` variables

<br />

### Locals Variables
- Tempary variables inside of the file / function body
- We can use outside of the files but can't use `locals` outside of the modules.
- They are `module specific`

- These are
    - Are computed once
    - Are not configurable from outside
    - Help make code cleaner, DRYer, and easier to read
 
- Define
```hcl
locals {
  app_name = "my-app"
  env      = "dev"
}
```

- Usage
```hcl
name = "${local.app_name}-${local.env}"
```

<br />

### Input Variables
- `Input variables` are used to parameterize your Terraform configurations
- They allow you to pass values into your modules or configurations from the outside
- There are some attributes to define input variables
    - `variable` - is used to declare an input variable named `example_var`
    - `description` - provides a human-readable description of the variable
    - `type` - specifies the data type of the variable (e.g., `string`, `number`, `list`, `map`, etc.)
    - `default` - provides a default value for the variable, which is optional

```hcl
variable "example_var" {
  description = "An example input variable"
  type        = string
  default     = "default_value"
}

<!-- we can use this variable with `var.example_var` -->
```

![Image](https://res.cloudinary.com/djgwvmcdl/image/upload/v1765912657/773272dc-91e9-431d-bb42-fa2a1855dad1.png)

In Terraform, `.tfvars` files are used to `assign values to input variables` so you don’t hard-code them in your configuration.

```hcl
# development.tfvars
region         = "us-east-1"
instance_count = 2
```

apply like this
```hcl
terraform plan  -var-file="dev.tfvars"
terraform apply -var-file="prod.tfvars"
```

Use `.tfvars for environment differences`

`.auto.tfvars` is a Terraform variable file that is automatically loaded without needing to pass -var-file on the command line. It’s mainly used to separate environment- or config-specific values while keeping Terraform runs simple. This has main priority than normal `tfvars` files.

<br />

📊 Variable Precedence Summary Table
| Priority   | Source                           |
| ---------- | -------------------------------- |
| 🔽 Lowest  | Variable defaults                |
|            | `TF_VAR_*` environment variables |
|            | `terraform.tfvars`               |
|            | `*.auto.tfvars`                  |
|            | `-var-file`                      |
| 🔼 Highest | `-var`                           |

<br />

### Output Variables
- `Output variables` allow you to expose values from your module or configuration, making them available for use in other parts of your Terraform setup
- There are some attributes to define output variables

```hcl
output "example_output" {
  description = "An example output variable"
  value       = resource.example_resource.example.id
} 

```






