This is a simple application to solve the second question within the Equal Experts Take Home Test
Parent
├── app
│   ├── app.py
│   ├── Dockerfile
│   ├── run_docker.sh
├── hello-deployment.yaml
├── hello-service.yaml
├── ReadMe.md
### 1. Create the app.py file with the hello world application
### 2. Dockerize the Python Application

Create a `Dockerfile` in the same directory as `app.py`:

### 3. Build the Docker Image

Run the shell script 'run_docker.sh' 

This will build the Docker image named `hello-python`.

### 4. Run Minikube

I have made the assumption that Minikube is already installed and running, so you would need to proceed with the following steps:

### 5. Deploy the Docker Image in Minikube

Apply the deployment in the 'hello-deployment.yaml' file using the script below:
```bash
kubectl apply -f hello-deployment.yaml
```

### 6. Deploy the load-balancing service for the deployment:

Deploy the service file named `hello-service.yaml` using the script below:
```bash
kubectl apply -f hello-service.yaml
```

### 7. Access the Service

In order to get access the service you need the Minikube IP:

```bash
minikube ip
```

Open a web browser or use a tool like `curl` to access `http://<minikube-ip>:<node-port>`. The `<node-port>` can be found using:

```bash
kubectl get services
```

If you are using VS Code look for the port under the `PORT(S)` column for `hello-python-service`.

You should see "Hello, World!" displayed, load balanced across the three replicas deployed within Minikube.


