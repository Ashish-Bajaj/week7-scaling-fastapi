# IRIS API – Kubernetes Autoscaling & CI/CD Deployment

**Dockerfile**  
Builds the container image for the IRIS FastAPI service. Installs dependencies and starts Uvicorn on port 8200.

**iris_log.py** 
Main FastAPI application with prediction endpoint and health probes. Handles logging, inference, and request tracing.

**requirements.txt**  
Lists all Python dependencies required to run the API. Installed during Docker build.

**deployment.yaml**  
Defines the Kubernetes Deployment that runs the IRIS API pods. Specifies container image, replicas, and probes.

**service.yaml**  
Creates a LoadBalancer service to expose the API externally. Routes port 80 to container port 8200.

**hpa.yaml**  
Configures Horizontal Pod Autoscaler. Automatically scales IRIS API pods based on CPU utilization.

**cd-gke.yml**  
GitHub Actions workflow that builds Docker images, pushes to Artifact Registry, deploys to GKE, and runs stress tests.

**model.joblib**  
Pretrained IRIS model used by the API for prediction. Loaded at startup inside the FastAPI service.
