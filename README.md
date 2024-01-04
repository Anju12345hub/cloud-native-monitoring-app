# cloud-native-monitoring-app


Things you will Learn
 1)Python and How to create Monitoring Application in Python using Flask and psutil 
 2)How to run a Python App locally. 
 3)Learn Docker and How to containerize a Python application 
     -Creating Dockerfile 
     -Building DockerImage 
     -Running Docker Container 
     -Docker Commands 
 4)Create ECR repository using Python Boto3 and pushing Docker Image to ECR
 5)Learn Kubernetes and Create EKS cluster and Nodegroups
 6)Create Kubernetes Deployments and Services using Python

Prerequisites ! 
(Things to have before starting the projects)

 - AWS Account. 
 - Programmatic access and AWS configured with CLI. 
 - Python3 Installed. 
 - Docker and Kubectl installed. 
 - eksctl installed Code editor (Vscode)

Let’s Start the Project ✨
 Part 1: Deploying the Flask application locally 
    Step 1: Clone the code Clone the code from the repository:

      git clone <repository_url> 
    Step 2: Install dependencies The application uses the psutil and Flask, Plotly, boto3 libraries. Install them using pip:

      pip3 install -r requirements.txt
    Step 3: Run the application 
      To run the application, navigate to the root directory of the project and execute the following command:

      python3 app.py
This will start the Flask server on localhost:5000. Navigate to http://localhost:5000/ on your browser to access the application.

Part 2: Dockerizing the Flask application 
    Step 1: Create a Dockerfile 
      Create a Dockerfile in the root directory of the project 
    Step 2: Build the Docker image 
      To build the Docker image, execute the following command:

      docker build -t <image_name> .
    Step 3: Run the Docker container 
      To run the Docker container, execute the following command:

       docker run -p 5000:5000 <image_name>
This will start the Flask server in a Docker container on localhost:5000. Navigate to http://localhost:5000/ on your browser to access the application.

Part 3: Pushing the Docker image to ECR 
    Step 1: Create an ECR repository 
      Create an ECR repository using Python: there is a file called ecr.py,run the following command to create an ecr repo

      python3 ecr.py
    Step 2: Push the Docker image to ECR Push the Docker image to ECR using the push commands on the console

Part 4: Creating an EKS cluster and deploying the app using Python
    Step 1: Create an EKS cluster Create an EKS cluster and add node group

    Step 2: Create a node group Create a node group in the EKS cluster.

    or

    Create the cluster and nodegroup by using eksctl 
    run the following command 
       eksctl create cluster --name <your_clustername> --region --node-type t2.micro --nodes-min2 --nodes-max 3

    Step 3: Create deployment and service there is a file called eks.py make sure to edit the name of the image with your image Uri.

Once you run this file by running “python3 eks.py” deployment and service will be created. 
Check by running following commands: 
    kubectl get deployment -n default (check deployments) 
    kubectl get service -n default (check service) 
    kubectl get pods -n default (to check the pods) 

    
Once your pod is up and running, run the port-forward to expose the service

kubectl port-forward service/<service_name> 5000:5000