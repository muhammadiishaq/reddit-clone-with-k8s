# Reddit Clone App on Kubernetes

## Project Overview

This project demonstrates how to deploy a **Reddit clone application** on Kubernetes and run it locally. The Reddit clone app mimics the basic functionalities of Reddit, such as creating posts and viewing content. The project uses **Docker** for containerization and **kind** (or Minikube) as the local Kubernetes cluster.  

The architecture includes:

- **Frontend & Backend Services** running as Kubernetes Deployments
- **Services** exposing Deployments internally
- **Port-forwarding** to access the app locally  

---

## Prerequisites

Before you begin, ensure you have the following installed on your local machine:

- [Docker](https://www.docker.com/)
- [kind](https://kind.sigs.k8s.io/) (or Minikube)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Git](https://git-scm.com/)

---

## Installation

Follow these steps to run the Reddit clone app locally:

1. **Clone the repository:**
```
git clone https://github.com/muhammadiishaq/reddit-clone-with-k8s.git
```
2. Navigate to the project directory:
```
cd reddit-clone-k8s-ingress
```

3. Build the Docker image:
```
docker build -t reddit-clone-app .
```

4. Optionally, push the Docker image to Docker Hub:
```
docker tag reddit-clone-app <your-dockerhub-username>/reddit-clone-app:latest
docker push <your-dockerhub-username>/reddit-clone-app:latest
```

4. Deploy the app to Kubernetes:
```
kubectl apply -f deployment.yaml
```

5. Deploy the Service for the app:
```
kubectl apply -f service.yaml
```
6. Access the app locally using port-forwarding:
```
kubectl port-forward svc/reddit-clone-service 8080:3000

```
7. Open your browser and go to:
```
http://localhost:8080/
```
## Architecture Diagram

```
User --> Service --> Deployment (Reddit Clone App)
```

1. Deployment: Runs the Reddit clone application as pods.

2. Service: Exposes the Deployment internally in the cluster.

3. Port-forwarding: Allows local access to the app without Ingress.

## Project Structure
```
reddit-clone-with-k8s/
├── project
├── Dockerfile
├── deployment.yaml
├── service.yaml
└── README.md
```

Dockerfile: Builds the Reddit clone app image.
deployment.yaml: Kubernetes Deployment configuration.
service.yaml: Kubernetes Service configuration.

## Contributing

Feel free to fork this repository, make improvements, and submit pull requests.

## License

This project is licensed under the MIT License.
