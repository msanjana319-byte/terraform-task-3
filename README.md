# Task 3: Infrastructure as Code (IaC) with Terraform

## Objective
Provision a local Docker container using Terraform, verify the deployment, inspect Terraform state, and destroy the infrastructure.

## Tools
- Terraform
- Docker Desktop
- Git and GitHub (for submission)

## What this project creates
- Pulls the `nginx:latest` Docker image if it is not already available.
- Creates a Docker container named `terraform-nginx`.
- Maps port `8080` on the computer to port `80` in the container.

After `terraform apply`, open http://localhost:8080 in a browser to verify that Nginx responds.

## Prerequisites
1. Install Docker Desktop and start it.
2. Install Terraform CLI.
3. Open PowerShell and check:
   ```powershell
   docker version
   terraform -version
   ```

## Run the project
Open PowerShell in this project folder and run these commands one at a time:

```powershell
terraform init
terraform fmt
terraform validate
terraform plan -out=tfplan
terraform apply tfplan
docker ps
terraform state list
terraform state show docker_container.nginx
```

Verify the website at `http://localhost:8080`.

## Destroy the resources
After taking the required screenshots and collecting logs, run:

```powershell
terraform destroy
```

Type `yes` when Terraform asks for confirmation. Confirm cleanup with:

```powershell
docker ps -a
terraform state list
```

The container should no longer be present, and the state list should be empty.

## Execution logs and screenshots
Save genuine command output in `execution-logs/`. Do not submit sample or fabricated output as if it came from your machine. Recommended evidence:
1. `terraform init` completed successfully.
2. `terraform plan` showing the planned resources.
3. `terraform apply` showing resources added.
4. `docker ps` showing `terraform-nginx` running and browser at `http://localhost:8080`.
5. `terraform state list`.
6. `terraform destroy` showing resources destroyed.

## Important
- Keep `terraform.tfstate`, `.terraform/`, `tfplan`, and any secrets out of GitHub. The `.gitignore` file excludes these.
- Run `terraform destroy` after verification if you do not want the test container to keep running.
