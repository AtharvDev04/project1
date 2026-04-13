# IaC Provisioning for Non-Profit System

A complete DevOps implementation for automating infrastructure provisioning of a Non-Profit system using Infrastructure as Code (IaC) tools like Terraform and Ansible, integrated with Docker, Kubernetes, and CI/CD pipelines.

---

## Project Overview

This project focuses on automating the provisioning and deployment of infrastructure for a Non-Profit system using modern DevOps practices. It leverages Infrastructure as Code (IaC) tools such as Terraform and Ansible to eliminate manual configuration errors and ensure consistent, repeatable deployments.

The system supports automated setup of local Docker environments or cloud-based infrastructure (e.g., AWS), along with CI/CD pipelines using GitHub Actions or Jenkins. Kubernetes is used for orchestration, enabling scalable and resilient deployments.

The key objective is to create a fully automated pipeline where infrastructure provisioning, application deployment, and scaling happen seamlessly with minimal human intervention.

---

## Key Features

- Infrastructure provisioning using Terraform and Ansible  
- Automated CI/CD pipeline using GitHub Actions / Jenkins  
- Docker-based containerization for consistent environments  
- Kubernetes orchestration for scalability and reliability  
- Script-based deployment for local and cloud environments  
- Eliminates manual configuration errors  
- Repeatable and scalable infrastructure setup  
- Supports both local Docker and cloud (AWS) deployment  

---

## Tech Stack

| Category | Technology |
|---|---|
| Infrastructure as Code | Terraform, Ansible |
| Containerization | Docker |
| Orchestration | Kubernetes (K8s) |
| CI/CD | GitHub Actions / Jenkins |
| Cloud | AWS (EC2, optional services) |
| Version Control | Git, GitHub |

---

## Project Structure

```

Deploy-Manufacturing-App-to-Kubernetes/
│
├── Dockerfile                        # Clones AI repo and runs Streamlit
├── requirements.txt                  # Clean Linux-compatible dependencies
├── .dockerignore                     # Files excluded from Docker build
├── .gitattributes                    # Git line ending rules for Linux
│
├── k8s/
│   ├── deployment.yaml               # Pods, replicas, rolling update config
│   └── service.yaml                  # AWS LoadBalancer service on port 80
│
└── .github/
    └── workflows/
        └── deploy.yml                # Full CI/CD pipeline definition
```

---

## Deployment Steps

### Prerequisites
- Git installed  
- Docker installed  
- Kubernetes (Minikube or cloud cluster)  
- Terraform installed  
- Ansible installed  
- AWS account (optional)  

---
**Step 1- Clone this repository**
```bash
git clone https://github.com/your-username/non-profit-iac.git
cd non-profit-iac
```


---

**Step 2- Provision Infrastructure using Terraform**

cd terraform  
terraform init  
terraform plan  
terraform apply  

Type yes to confirm. Provisions required infrastructure automatically.


---

**Step 3-  Configure Infrastructure using Ansible**
```bash
cd ../ansible
ansible-playbook -i inventory.ini playbook.yml
```

---

**Step 4- Run Docker Environment**
```
bash
cd ../docker
docker-compose up -d
```
---


**Step 5- Deploy to Kubernetes**

Apply Kubernetes configuration files::
```
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```
---

**Step 6- Add GitHub Secrets**

Go to your GitHub repo → Settings → Secrets and variables → Actions and add:
```

AWS_ACCESS_KEY_ID      → your IAM user access key
AWS_SECRET_ACCESS_KEY  → your IAM user secret key
DOCKER_USERNAME        → your Docker Hub username
DOCKER_PASSWORD        → your Docker Hub access token
KUBE_CONFIG            → your kubeconfig file (base64 encoded)
```



---

**Step 7-  Configure Infrastructure using Ansible**
```bash
Push to trigger the pipeline
```
Go to the Actions tab on GitHub and watch all stages complete. The pipeline builds the image, provisions infrastructure, and deploys to Kubernetes automatically.


---

**Step 8-  Get the app URL**
```bash
kubectl get services

Copy the EXTERNAL-IP value and open http://EXTERNAL-IP in any browser.

```

---





## CI/CD Pipeline Stages

```
Stage 1 — Checkout
└─ Pull latest code from repository

Stage 2 — Build
└─ Build Docker image

Stage 3 — Test
└─ Run validation checks

Stage 4 — Push
└─ Push Docker image to registry

Stage 5 — Provision
└─ Run Terraform scripts

Stage 6 — Configure
└─ Execute Ansible playbooks

Stage 7 — Deploy
└─ Deploy to Kubernetes cluster

Stage 8 — Verify
└─ Check pod and service status
```


---

## Scalability & Automation

- Infrastructure is fully automated using IaC  
- Kubernetes ensures horizontal scaling  
- CI/CD enables continuous delivery  
- Easily reproducible environments  

---

## GitHub Secrets Required

Before the pipeline can run, these secrets must be added to the repository under Settings → Secrets and variables → Actions:

`AWS_ACCESS_KEY_ID`  
`AWS_SECRET_ACCESS_KEY`  
`DOCKER_USERNAME`  
`DOCKER_PASSWORD`  
`KUBE_CONFIG`  

(For Kubernetes cluster access)

`TERRAFORM_BACKEND_CONFIG`  

(For managing Terraform state remotely, optional)

`ANSIBLE_HOST_KEY_CHECKING`  

(Set to False if required for automation)




---

## Future Enhancements

- Monitoring with Prometheus & Grafana  
- Auto-scaling in Kubernetes  
- Centralized logging (ELK stack)  
- Improved security with IAM roles  

---

## Group Members

| Sr No | Name | Enrollment Number |
|---|---|---|
| 01 | Anushka Kashyap | EN22CS301180 |
| 02 | Ananya Subramanya Rao | EN22CS301120 |
| 03 | Atharv Chaturvedi | EN22CS301228 |
| 04 | Harshit Panchal | EN23CS3L1010 |
| 05 | Anirudh Vyas | EN22CS301131 |

---

- Institution:  Medicaps University, Datagami Skill Based Course
- Industry Mentor- Prof. Akshay Saxena
- Academic Year: 2025-2026  
- Project Type: DevOps / Cloud Computing
 
