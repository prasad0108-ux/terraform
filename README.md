📦 **Project Title**: Terraform + Docker: Local Container Provisioning

This project demonstrates how to provision and manage a Docker container locally using Terraform as Infrastructure as Code (IaC).

---

🎯 **Objective**  
Provision a local Docker container using Terraform, access it via browser, and destroy it — following the full Terraform lifecycle directly on your local system.

---

🛠️ **Tools Used**

- 🟩 Terraform – To define infrastructure as code  
- 🐳 Docker – To build and run containers locally  
- 💻 Windows Command Prompt – Execution environment

---

🔁 **Terraform Lifecycle & Commands**

1️⃣ **Write Configuration**  
You define the infrastructure in a file named main.tf, which includes:  
• Docker provider configuration  
• Docker image (e.g., nginx)  
• Docker container with port mapping  

2️⃣ **Initialize Terraform**  
Command: terraform init  
- Initializes the working directory and installs the necessary Docker provider plugin

3️⃣ **Plan the Deployment**  
Command: terraform plan  
- Shows you what Terraform will create or change before it does anything

4️⃣ **Apply the Configuration**  
Command: terraform apply  
- Pulls the Docker image and spins up the container  
- You’ll be prompted to confirm with a “yes”

5️⃣ **Access the Application**  
- Open your browser and go to: http://localhost:8080  
- This will show the nginx welcome page or whichever app you’ve configured

6️⃣ **Destroy Infrastructure**  
Command: terraform destroy  
- Tears down the Docker container and cleans up all resources

---

📁 **Key Terraform Configuration File – main.tf**

terraform  
  required_providers  
    docker  
      source  = "kreuzwerker/docker"  
      version = "~> 3.0.1"  


provider "docker"  
  host = "npipe:////.//pipe//docker_engine"  


resource "docker_image" "nginx"  
  name         = "nginx:latest"  
  keep_locally = false  


resource "docker_container" "nginx"  
  image = docker_image.nginx.image_id  
  name  = "nginx_container"  
  ports  
    internal = 80  
    external = 8080  

---

📸 **Suggested Screenshots to Include in Documentation**

- ✅ Output of `terraform init`  
- ✅ Output of `terraform apply` showing container creation  
- ✅ Browser screenshot accessing app via http://localhost:8080  
- ✅ Output of `terraform destroy` confirming removal

---

📄 **Deliverables**

- main.tf – Terraform configuration  
- terraform.log – Optional execution log  
- Screenshots – One per key step in the lifecycle

---

🙋‍♂️ **Author**

Prasad  
DevOps Learner | Focused on automation using Terraform and Docker  
GitHub: https://github.com/prasad0108-ux

---
