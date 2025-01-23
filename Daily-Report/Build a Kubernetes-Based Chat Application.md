# Kubernetes-Based Chat Application Report

### Name: Sourabh  
### Date: 20 Dec  
### Project Title: Build a Kubernetes-Based Chat Application
### Epic Name:  KUBERNATIVES
### Git Link: https://github.com/srbhcodes/my-k8s-project

---

## Scope of Project
The purpose of this project was to create a scalable and containerized chat server application deployed on a Kubernetes cluster. The application provides an API for sending and retrieving messages and is integrated with a Redis database for storing chat data. It demonstrates how to manage microservices efficiently using Kubernetes.

---

## Technologies Used
- **Programming Languages**: Python (Flask) / JavaScript (Node.js, Express)
- **Containerization**: Docker
- **Container Orchestration**: Kubernetes (Minikube)
- **Database**: Redis
- **Networking**: NodePort service for external access
- **Version Control**: Git
- **Tools**: curl, Minikube, kubectl

---

## Steps
1. **Setup Development Environment**:
   - Installed necessary dependencies (Flask/Node.js, Redis client).
   - Configured Docker for containerization.

2. **Application Development**:
   - Created REST API endpoints `/api/messages` (GET) and `/api/send` (POST).
   - Integrated Redis for message storage.

3. **Containerization**:
   - Built Docker images for the chat server and Redis.
   - Uploaded Docker images to a container registry.

4. **Kubernetes Deployment**:
   - Created Kubernetes manifests for:
     - Chat server deployment and service.
     - Redis deployment and ClusterIP service.
   - Used `kubectl` to apply configurations.

5. **Testing**:
   - Tested the chat server on local Kubernetes using Minikube.
   - Used curl commands to validate API functionality.

6. **Version Control**:
   - Uploaded all project files, including Kubernetes manifests, Dockerfiles, and source code, to a Git repository.

---

## Project Outcome
- Successfully deployed a Kubernetes-based chat application with a Redis database.
- The application is accessible via a NodePort service at `http://<minikube-ip>:<nodeport>`.
- The APIs for sending and retrieving messages are functional.

---

## Issues Faced
1. **API Not Responding**:
   - Encountered `Cannot GET /api/messages` and `Cannot POST /api/send`.
   - Resolved by debugging Flask/Express routes and ensuring proper configuration.

2. **Minikube Networking**:
   - Initially faced difficulty accessing the application through the NodePort.
   - Verified Minikube IP and NodePort configuration.

3. **Service Misconfiguration**:
   - Redis service was not accessible due to incorrect `ClusterIP` setup.
   - Corrected Redis service configuration in Kubernetes.

4. **Pod Logs and Debugging**:
   - Inspected logs using `kubectl logs` to debug issues in chat server deployment.
   - Found missing route handling errors and fixed them.

5. **Containerization Challenges**:
   - Faced issues with Dockerfile configurations for the chat server.
   - Resolved by verifying dependencies and entrypoints.

6. **Git Repository Setup**:
   - Uploaded project files to Git with proper directory structure and documentation.

---
### Screenshots

Minikube cluster running:

![[Pasted image 20250107211617.png]]

![[Pasted image 20250107211810.png]]

verified that if its running:
![[Pasted image 20250107211831.png]]

Running:
![[Pasted image 20250107212047.png]]

Running:
![[Pasted image 20250107212130.png]]