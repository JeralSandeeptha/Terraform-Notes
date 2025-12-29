# Validations

Terraform validations are rules you define to validate user input before Terraform creates resources.

They help you:
  - Prevent wrong values ❌
  - Fail early (before apply) 🚨
  - Enforce standards (naming, CIDR ranges, regions, etc.) 🛡️

Validations run during:
  - `terraform plan`
  - `terraform apply`

Terraform validations are mainly used in `variables block` 

This is the basic syntax
```hcl
variable "example" {
  type = string

  validation {
    condition     = <BOOLEAN_EXPRESSION>
    error_message = "Error message shown to the user"
  }
}
```

Key rules are,
  - condition must evaluate to true
  - If `false` → Terraform stops execution
  - `error_message` must be a static string
