# Full-Stack Chat Application on Minikube

This repository provides a full-stack chat application using **React** for the frontend, **Node.js** (Express) for the backend, and **MongoDB** for data storage. The project is containerized using **Docker** and orchestrated with **Kubernetes** on a **Minikube** cluster.

## Features:
  - Real-time Messaging: Send and receive messages instantly using Socket.io
  - User Authentication & Authorization: Securely manage user access with JWT
  - Scalable & Secure Architecture: Built to handle large volumes of traffic and data
  - Modern UI Design: A user-friendly interface crafted with React and TailwindCSS
  - Profile Management: Users can upload and update their profile pictures
  - Online Status: View real-time online/offline status of users

## Technologies Used

- **Frontend**: React, Tailwind CSS
- **Backend**: Node.js (Express)
- **Database**: MongoDB
- **Containerization**: Docker
- **Orchestration**: Kubernetes (Minikube)
- **Authentication**: JWT (JSON Web Tokens)
- **Persistent Storage**: MongoDB Persistent Volume

## Prerequisites

Before you begin, ensure you have the following installed on your machine:

- Docker
- Minikube
- kubectl
- Node.js

If Minikube is not set up yet, you can follow the setup instructions in my [Minikube Cluster Setup](https://github.com/chiragpuniyanii/Minikube-Cluster-Setup) repository.

## Steps to Set Up

### 1. Clone the Repository

First, clone the repository and navigate into the project directory:

```bash
git clone https://github.com/chiragpuniyanii/Full-Stack-Chat-Application-on-Minikube.git
cd full-stack-chat-app
```

### 2. Docker Setup
**Backend**

Navigate to the backend folder:

```bash
cd backend
```
Build the Docker image for the backend:

```bash
docker build -t chiragg619/chatapp-backend:latest .
```
Push the Docker image to Docker Hub:

```bash
docker push chiragg619/chatapp-backend:latest
```
**Frontend**

Navigate to the frontend folder:

```bash
cd ../frontend
```
Build the Docker image for the frontend:

```bash
docker build -t chiragg619/chatapp-frontend:latest .
```
Push the Docker image to Docker Hub:

```bash
docker push chiragg619/chatapp-frontend:latest
```
**MongoDB**

Pull the MongoDB Docker image from Docker Hub:

```bash
docker pull mongo
```


### 3. Minikube Kubernetes Setup
**Start Minikube**
Start Minikube to set up a local Kubernetes cluster:

```bash
minikube start
```
**Create Namespace**
Create a Kubernetes namespace for your project:

```bash
kubectl create -f k8s/namespace.yml
```
**MongoDB Persistent Volume**
Apply the Persistent Volume (PV) configuration for MongoDB:

```bash
kubectl apply -f k8s/mongo-pv.yml
```
**MongoDB Persistent Volume Claim**
Apply the Persistent Volume Claim (PVC) for MongoDB:

```bash
kubectl apply -f k8s/mongo-pvc.yml
```
**MongoDB Deployment**
Deploy MongoDB on Kubernetes:

```bash
kubectl apply -f k8s/mongo-deployment.yml
```
**Backend Deployment**
Deploy the backend application on Kubernetes:

```bash
kubectl apply -f k8s/backend-deployment.yml
```
Optional: Replace your JWT secret in the secrets.yml file.
```bash
kubectl apply -f k8s/secrets.yml
```
**Backend Service**
Apply the backend service configuration to expose the backend:

```bash
kubectl apply -f k8s/backend-service.yml
```
**Frontend Service**
Apply the frontend service configuration to expose the frontend:

```bash
kubectl apply -f k8s/frontend-service.yml
```
**Frontend Deployment**
Deploy the frontend application on Kubernetes:

```bash
kubectl apply -f k8s/frontend-deployment.yml
```

### 4. Verify Setup
To check the services and pods in your chat-app namespace:

```bash
kubectl get svc -n chat-app
kubectl get pods -n chat-app
```
### 5. Port Forwarding
To access the application locally, use port forwarding for both the backend and frontend:

**Backend Port Forwarding**
To run the backend in the foreground:

```bash
kubectl port-forward service/backend -n chat-app 5001:5001
```
To run the backend in the background:

```bash
kubectl port-forward service/backend -n chat-app 5001:5001 &
```
**Frontend Port Forwarding**
To run the frontend in the foreground:

```bash
kubectl port-forward service/frontend -n chat-app 80:80
```
To run the frontend in the background:

```bash
kubectl port-forward service/frontend -n chat-app 80:80 &
```
Note: If you encounter "permission denied" errors, use sudo:

```bash
sudo kubectl port-forward service/frontend -n chat-app 80:80 &
```
### 6. Access the Application
Once port forwarding is successful, you can access the application:

Frontend: http://localhost:80

Backend: http://localhost:5001

<img width="1440" alt="logout" src="https://github.com/user-attachments/assets/fb8e0375-2f22-496a-90a5-a7d89e19d5ba" />




### 7. Project Structure
Here’s the structure of the project:

```bash
.
├── backend/                # Node.js backend with Express
│   └── Dockerfile          # Dockerfile for backend
├── frontend/               # React + Tailwind CSS frontend
│   └── Dockerfile          # Dockerfile for frontend
├── k8s/                    # Kubernetes configuration files
│   ├── namespace.yml       # Kubernetes namespace definition
│   ├── mongo-pv.yml        # Persistent volume configuration for MongoDB
│   ├── mongo-pvc.yml       # Persistent volume claim for MongoDB
│   ├── mongo-deployment.yml # MongoDB deployment configuration
│   ├── backend-deployment.yml # Backend deployment configuration
│   ├── backend-service.yml # Backend service configuration
│   ├── frontend-deployment.yml # Frontend deployment configuration
│   └── frontend-service.yml # Frontend service configuration
├── Dockerfile              # Dockerfile for building images
└── README.md               # Project documentation
```
### Contributing
Feel free to fork the repository, make changes, and submit a pull request with your improvements.

### License
This project is licensed under the MIT License.

### Contact
  - For inquiries or feedback, please contact:
  - Chirag Puniyani
  - Email: chiragpuniyani7@gmail.com

```csharp

This is the complete `README.md` for your full-stack chat application with Minikube and Docker. You can copy-paste this into your `README.md` file in your repository.
```






