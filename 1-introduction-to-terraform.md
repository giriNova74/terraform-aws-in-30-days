# Introduction to Terraform & Infrastructure as Code (IaC)

Welcome to the foundation of this **Terraform AWS in 30 Days** journey.

Before writing a single line of Terraform code, it is important to understand **what Infrastructure as Code (IaC) is**, **why it exists**, and **why Terraform is the most preferred IaC tool in modern Cloud & DevOps engineering**.

---

## What is Infrastructure as Code (IaC)?

**Infrastructure as Code (IaC)** is the practice of managing and provisioning infrastructure through **machine-readable configuration files**, rather than manual hardware configuration or interactive UI changes.

Instead of clicking in the AWS Console, you write code to create:

- VPC
- EC2
- Load Balancers
- Databases
- Kubernetes clusters
- IAM roles

Infrastructure becomes **version-controlled**, **repeatable**, and **automated**.

---

## Why Do We Need IaC?

Traditional infrastructure management problems:

- Manual configuration leads to mistakes
- No version history of infrastructure changes
- Difficult to replicate environments
- Time-consuming deployments
- Configuration drift between environments

IaC solves this by providing:

- Automation
- Consistency
- Version control (Git)
- Faster deployments
- Disaster recovery through code
- Environment reproducibility

---

## Popular Infrastructure as Code Tools

| Tool | Provider | Language | Cloud Support |
|------|----------|----------|---------------|
| AWS CloudFormation | AWS | JSON/YAML | AWS only |
| Azure ARM / Bicep | Microsoft | JSON/Bicep | Azure only |
| Google Deployment Manager | GCP | YAML | GCP only |
| Ansible | RedHat | YAML | Multi-cloud |
| Pulumi | Pulumi | Python/TS/Go | Multi-cloud |
| **Terraform** | HashiCorp | HCL | **Multi-cloud** |

---

## Why Terraform is the Best Choice

Terraform stands out because:

- Cloud agnostic (AWS, Azure, GCP, Kubernetes, GitHub, etc.)
- Declarative language (HCL) that is easy to read
- Massive provider ecosystem
- State management
- Reusable modules
- Strong community support
- Works perfectly with CI/CD pipelines
- Industry standard for DevOps & Platform Engineering

---

## IaC Architecture (How It Works)

IaC tools like Terraform follow this flow:

1. You write configuration files (`.tf`)
2. Terraform reads the desired state
3. It compares with current infrastructure
4. Creates an execution plan
5. Applies only the necessary changes
6. Stores state for future comparison

This ensures **idempotency** and **predictable infrastructure changes**.

---

## Important Terraform (IaC) Commands

| Command | Purpose |
|---------|---------|
| `terraform init` | Initialize project and download providers |
| `terraform validate` | Validate configuration syntax |
| `terraform fmt` | Format Terraform files |
| `terraform plan` | Preview infrastructure changes |
| `terraform apply` | Create/update infrastructure |
| `terraform destroy` | Delete infrastructure |
| `terraform show` | Show current state |
| `terraform state list` | List resources in state |
| `terraform output` | Show output variables |
| `terraform workspace` | Manage multiple environments |

---

## Key Concepts You Will Learn

- Providers
- Resources
- Variables
- Outputs
- State file
- Remote backend
- Modules
- Workspaces

---

## Summary

Infrastructure as Code is the backbone of modern Cloud engineering.

Among all IaC tools, **Terraform** is the most powerful, flexible, and widely adopted solution that enables engineers to build production-grade infrastructure using code.

This 30-day journey will help you master Terraform by building real AWS infrastructure step by step.
