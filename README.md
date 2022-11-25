# **Introduction**

Here are the challenges of the second phase of the DevOps Enginner role for ElectroNeek Robotics.

## **Description**

We have three challenges to deliver:

* **Creation of the base infrastructure**
* **Backend**
* **Front-End**

There is no cake recipe to achieve the objective of the challenge, but we have good practices that will be evaluated along with the codes that must be well documented.

**How ​​to deliver these challenges:**
You must create a repository on your GitHub/GitLab, push your solution and send the repository link along with your LinkedIn and CV (updated) to the recruiter's email. Remembering that the implementation must be in folders in a structured way on GitHub/GitLab so that we have easy identification. It is recommended that you commit your application following the GitFlow flow and with the **Conventional Commits** specifications.

A differential is to add informative content that it deems useful to the project, such as a description of the application in the README with instructions on how to run it.

Remember to consider best practices as you would a production environment.

## **Scope**

ElectroNeek Robotics is migrating its infrastructure from Classic Infrastructure to Public Cloud. It wants to utilize all the benefits that distributed computing offers such as scalability, elasticity, cost savings, security, and rapid provisioning. Currently, the company has a monolithic application running on a single server and wants to segment it into microservices. It will be necessary to create a new network to host the applications, segment the current ElectroNeek Robotics application into Front-end, Back-end and Database in containers, provision resources using IaC, promote high availability and provide observability for the applications.

You are the person responsible for performing the migration. You can choose between any cloud provider to complete the challenge.

Remembering that cloud infrastructure resources must always be created using configuration managers, such as CloudFormation, Terraform or Ansible, ensuring that every resource can be easily versioned and recreated. You must choose between Cloudformation, Terraform or Ansible to take the challenge.

## **Challenge 00: Creation of base infrastructure**

Your application will run in the cloud and needs a properly configured VPC to run. Create a VPC with three private subnets and three public subnets. Private ones cannot be accessed directly from the external network, public ones must be exposed publicly with due care. Your network will be small, choose a suitable IP range and justify it. The VPC must be created using IaC.

## **Challenge 01: Backend**

### **Need**

You've been granted access to the ElectroNeek Robotics monolith and it's time to segment it into microservices. The application must offer three isolated layers: Front-end, Back-end and Database. The services must run on Linux servers and in containers using Kubernetes.

Remembering that currently Kubernetes is the main tool for orchestration and deployment of containers used in the world, practically becoming a standard for abstraction of infrastructure resources.

At Let’s Code by Ada, all our services will be containerized and distributed in clusters for each environment, so it is important that applications are adaptable to each environment and that there is control via code of Kubernetes resources through their manifests.

Communication between components must be performed via HTTP and the use of queues in the flow will be a differential.

### **Objective**

Create a Linux instance on the chosen Cloud provider using CloudFormation, Terraform or Ansible.
Pre-install Java and its dependencies on the instance so that it automatically uploads the Let’s Code by Ada application API.

The instance should only open to ports 8080 and 443 to the internet. The SSH port (22) must be accessible only for a defined IP range.

Choose a relational database of your choice and open its respective port to connect to the application. The database must run on a PaaS from your Cloud provider.

Inside the repository in the **back-end** folder you will find the Java API code. You must turn this code into a **Dockerfile** and get the application running.

The application needs to connect to a database and the connection takes place through the **application.yml** file in the **resources** folder. After pointing the environment variables to the database correctly, Spring will automatically create the **user** table needed to follow the challenge. You must fill in the application's environment variables following the example below.

![Application Backend Java](https://s3-sa-east-1.amazonaws.com/lcpi/f0d632a4-3e51-4d7f-9c18-5c75a257dc51.PNG)

After configuring the back-end and the database, it is necessary to create a user to access the application. Access the database in the easiest way and create a user. It will be necessary to inform the **username** and **password**.

## **Challenge 02: Frontend**

### **Need:**

After migrating the back-end of the Let’s Code by Ada application to the cloud, it’s time to work with the front-end. You should think about the best cloud service to run the front end with in mind scalability, ease of maintenance and cost optimization. On AWS a good choice for this service might be S3, but feel free to run this application on another service and cloud provider.

### **Objective:**

Inside the repository in the **frontend** folder you will find the application code in Angular. You must turn this code into a **Dockerfile** and get the application running. Remember that to install the application's dependencies just apply the command **npm install** and to run it use the command **ng serve**.

You must change the pointer to the backend through the **environment.ts** file in the **src/environments** folder.

![Angular Envitoment](https://s3-sa-east-1.amazonaws.com/lcpi/a14aa61a-5197-445d-aef4-9c2ad64715ad.PNG)

The application must be called via DNS, feel free to use a domain of your choice.

After configuring the application, perform the deployment and the login screen should be displayed.

Log in with the user created in the backend challenge.

**Having completed all the steps, the challenge is over!**

### **Grades:**

Inside the challenge repository there are two folders, backend and frontend, in each folder you will find an app subdirectory, your objective is:

* Build the application's docker image;
* Create the kubernetes resource manifests to run the application *(deployments, services, ingresses, configmap and any others you deem necessary)*;
* Create a script to execute the deploy in a single execution;
* The application must be deployed on a single command line on a local Kubernetes cluster;
* All pods must be running;
* The application must respond to a specific URL configured in the ingress;
* The application starts up by default using port 3000 and uses an environment variable $NAME.

Remembering that:

* You can use both AWS, Azure or GCP, you don't need to run the test on both, just one;
* All resources must be created using free AWS/Azure/GCP credits;
* Don't forget to destroy the resources after creating and testing the challenge to avoid charges or depletion of credits.

### **Extras (differential):**

* Use HELM;
* Division of resources by namespaces;
* Use of health check in the application;
* Use of Terraform modules;
* Perform the deployment through a CI/CD pipeline;
* Set up a small observability of the application's infrastructure with a tool of your choice;
* Make the application display your name instead of "May the force be with you!".

**Success!!**
