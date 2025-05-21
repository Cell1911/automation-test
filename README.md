# 🚀 Automation Test Project

This project demonstrates a complete Infrastructure as Code pipeline that deploys a static web application using:

- **Terraform** (provisioning on AWS)
- **Ansible** (server configuration & deployment)
- **Docker** (containerizing the app)
- **GitHub Actions** (CI/CD)

---

## 📁 Project Structure

automation-test-main/
├── .github/workflows/build.yml # CI/CD pipeline with GitHub Actions
├── Dockerfile # Docker image for static app
├── index.html # Web app content (static HTML)
├── my-key.pub # SSH public key (for EC2)
├── ansible/ # Ansible configuration
│ ├── deploy.yml # Ansible playbook
│ ├── inventory.ini # Hosts inventory (target: EC2)
│ ├── my-key # SSH private key for EC2 (DO NOT SHARE)
│ └── vars.yml # Deployment variables
└── terraform/ # Terraform scripts for AWS
├── ec2_ip.txt # Output of EC2 public IP
├── main.tf # Main infrastructure config
├── output.tf # Output declarations
├── terraform.tfvars # Variables with values
└── variables.tf # Variable declaration


---

## ✅ Prerequisites

You need the following installed locally:

- [Terraform](https://developer.hashicorp.com/terraform/install)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/)
- [Docker](https://docs.docker.com/get-docker/)
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- A configured AWS IAM user with access to EC2

---

cd terraform

# Initialize Terraform
terraform init

# Preview infrastructure
terraform plan

# Apply to create EC2
terraform apply

## Configure Server with Ansible

cd ansible

ansible-playbook -i inventory.ini deploy.yml

## CI/CD with GitHub Actions
The .github/workflows/build.yml automatically builds the Docker image and pushes it (to Docker Hub or another registry).

You can extend this to trigger deployments using Ansible or Terraform CLI via GitHub runners or self-hosted runners.


## we tried to capture IP here and deploy the image but adding terraform in this was not logical so you guys can build arch using terraform and then use this project to further CI/CD



