## Comments
- Single Line Comments
```hcl
# This is a single line comment
```

- Multiline Line Comments
```hcl
/*
# This is a single line comment
*/
```

## Blocks
- Blocks are container for other contents
- These are the basic block types:
    - `terraform` block
    - `provider` block
    - `resource` block
    - `variable` block
    - `locals` block
    - `data` block
    - `module` block
    - `output` block
    - `provisioner` block

```hcl
block_type {
    attribute1 = value1
    attribute2 = value2
}
```

## Attributes
- Attributes are just key-value pairs

```hcl
key = value
```

## Datatypes
- Datatypes are used to define the type of that data
- These are the main datatypes
    - `string` -> "jeral"
    - `number` -> 2
    - `boolean` -> false
    - `List` -> ["item1", "item2", "item3"]
    - `Maps` -> { key: value }

## Conditions
- Conditions are used to set dynamic data depending on the scenario
- We use `ternnary operator` which is `condition ? true_val : false_val`

```hcl
variable "create_bucket" {
  type    = bool
  default = true
}

resource "aws_s3_bucket" "example" {
  count = var.create_bucket ? 1 : 0
  bucket = "my-conditional-bucket"
}
```

```hcl
variable "env" {
  type    = string
  default = "dev"
}

resource "aws_instance" "example" {
  ami           = "ami-123456"
  instance_type = var.env == "prod" ? "t3.large" : "t3.micro"
}
```

## Functions
- Functions are used to create reusable peice of codes
- There are some of the `built-in` functions

```hcl
resource "aws_s3_bucket" "example" {
  bucket = "${lower(var.env)}-app-bucket"
}
```

## Resourcedependency
- This is used to create a relationship between two resources
- There are two types of dependencies 
    - `Implicit Dependencies`
    - `Explicit Dependencies`
