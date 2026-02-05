# Day 2 — Terraform Providers, Versioning, and Complete Local Setup (WSL + VS Code + AWS CLI + Terraform)

Today you will build the **complete local environment** required for real-world Terraform + AWS work.

This is exactly how Cloud & DevOps engineers set up their machines.

---

## What is a Terraform Provider?

A **Terraform Provider** is a plugin that allows Terraform to interact with APIs of platforms like AWS, Azure, GCP, Kubernetes, GitHub, etc.

Without a provider, Terraform cannot talk to any cloud.

Example:

```hcl
provider "aws" {
  region = "us-east-1"
}
```
Two types of versioning control stability in projects:

1. Terraform Version

Defines which Terraform binary version should run your code.
```
terraform {
  required_version = ">= 1.5.0"
}
```
Prevents your code from breaking on older/newer Terraform versions.
2. Provider Version

Locks the AWS provider version.
```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}
```
~> 5.0 means:

Allow 5.x

Do not allow 6.x (breaking changes)

This is critical in real projects.

Local Environment Setup (Ubuntu WSL)
Update system
```
sudo apt update && sudo apt upgrade -y

```
Install basic tools
```
sudo apt install -y wget curl unzip git software-properties-common

```
Install Java (required for many AWS tools & Jenkins later)
```
sudo apt install -y openjdk-17-jdk
java -version
```
Install AWS CLI
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
```
Install Terraform
```
wget https://releases.hashicorp.com/terraform/1.6.6/terraform_1.6.6_linux_amd64.zip
unzip terraform_1.6.6_linux_amd64.zip
sudo mv terraform /usr/local/bin/
terraform -version
```
VS Code + WSL Extension

Install VS Code on Windows

Install WSL extension

Open WSL terminal

Run:
```
code .
```
Validate Installations

Run all:
```
java -version
aws --version
terraform -version
git --version
```
Configure AWS IAM User for CLI & Terraform

Create an IAM user with:

Programmatic access

Add to Development group

Download Access Key & Secret.

Then run:
```
aws configure
```
verify connection 
```
aws sts get-caller-identity
aws configure list
```
