# Introduction to IaC and Terraform

## 📌 What is Infrastructure as Code (IaC)?
- `Infrastructure as Code (IaC)` is the practice of `managing` and `provisioning` computing `infrastructure` through machine-readable configuration files, rather than through physical hardware or interactive configuration tools (like the AWS Console)
- `Instead of manually configuring servers, networks, databases, etc., you write code (usually in JSON, YAML, or domain-specific languages like HCL) to define your infrastructure. This enables automation, versioning, consistency, and repeatability`
- If we write code for one cloud provider and if we want to change that we can do that. It is doing by calling their respective providers APIs. So that's why we called this as a `API as Code` also

<br />

### Benefits of IaC:
- ✅ `Consistency`: Avoid configuration drift between environments
- ✅ `Automation`: Reuse scripts to deploy infrastructure
- ✅ `Version Control`: Use Git to track and review changes
- ✅ `Speed`: Provision entire infrastructures in minutes
- ✅ `Scalability`: Scale resources up/down quickly and safely

<br />

## 📌 Why Use Terraform?
- `Terraform` is a popular open-source `IaC tool` created by `HashiCorp`.
- It uses a `declarative language` called `HCL` (HashiCorp Configuration Language)
- Any cloud providers have their own IaC tools but with terraform if we learn at once we can write for any cloud provider 

<br />

###  Key reasons to use Terraform:
- ☁️ `Multi-Cloud Support`: Works with AWS, Azure, GCP, and many other providers
- 🧱 `Modular`: Supports reusable modules for better maintainability
- ⚙️ `Declarative`: You describe the desired state, and Terraform handles how to reach it
- 📁 `State Management`: Maintains a state file to track infrastructure
- 🔁 `Execution Plan`: terraform plan shows what will change before applying
- 🔌 `Large Ecosystem`: Thousands of community modules and providers

| Feature              | Terraform          | Ansible                               | CloudFormation        | Pulumi                               |
| -------------------- | ------------------ | ------------------------------------- | --------------------- | ------------------------------------ |
| **Type**             | IaC (Declarative)  | Configuration Management (Procedural) | IaC (Declarative)     | IaC (Imperative with real languages) |
| **Language**         | HCL                | YAML + Python                         | JSON / YAML           | TypeScript, Python, Go, etc.         |
| **Multi-Cloud**      | ✅ Yes              | ✅ Yes                                 | ❌ AWS only            | ✅ Yes                                |
| **State Management** | ✅ Yes (Built-in)   | ❌ No                                  | ✅ Yes                 | ✅ Yes                                |
| **Use Case**         | Infra provisioning | App config + server setup             | AWS-only provisioning | Infra provisioning with real code    |
| **Complexity**       | Moderate           | Low                                   | Moderate              | High (programmer-friendly)           |

- Use `Terraform` for provisioning infrastructure across clouds
- Use `Ansible` for post-provisioning and configuration (e.g., installing software)
- Use `CloudFormation` if you're AWS-only and want native tooling
- Use `Pulumi` if you prefer real programming languages

<br />

### How to provision infrasturcture?
![Image](https://res.cloudinary.com/djgwvmcdl/image/upload/v1765694646/ac7ddc03-c979-4234-95b6-6cda6d88d2de.png)


<br />

### Benefits
![Image](https://res.cloudinary.com/djgwvmcdl/image/upload/v1765694686/55aed99e-bb21-47b9-9a07-babcdf10d898.png)
![Image](https://res.cloudinary.com/djgwvmcdl/image/upload/v1765694710/bfb154e3-553e-44a5-b3a9-c17549ee10d6.png)
