## Variables
- Variables in Terraform are essential for parameterizing and sharing values within your Terraform configurations and modules
- They allow you to make your configurations more dynamic, reusable, and flexible

- There are 2 types of variables
    - `Input` variables
    - `Output` variables

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

### Output Variables
- `Output variables` allow you to expose values from your module or configuration, making them available for use in other parts of your Terraform setup
