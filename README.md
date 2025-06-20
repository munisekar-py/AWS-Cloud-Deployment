# AWS-Cloud-Deployment
Simple MERN stack application deployment


##**Cloud-Deployment-Project**
This project involves deploying the MERN-based ( (MongoDB, Express.js, React, Node.js) Travel Memory app on Amazon EC2. It focuses on full-stack cloud deployment, backend and frontend configuration, and building a scalable architecture using tools like AWS Load Balancer, Target Groups  and Cloudflare.

Project Repository: https://github.com/UnpredictablePrashant/TravelMemory

##**Objectives or goals of this project:**

  Creating Frontend,Backend EC2 instances and MongoDB.

  Configuring the backend and connecting it with a MongoDB instance.

  Configuring frontend and linking it to the backend.

  Implementing load balancing to divide traffic.

  Integrating a custom domain using Cloudflare.

###**Provisioning EC2 Instances:**

Log in to AWS Management Console.
  Navigate to EC2 Dashboard and click "Launch Instance".
  Choose Ubuntu Server as the OS, instance type and key pair for SSH access.
  Configure Security Group to allow ports 22 (SSH), 80 (HTTP), 443 (HTTPS), and 3000 (backend).
  Launch the instance. Repeat the same steps to again one instance for Backend and one for Front end.

###**Setting Up MongoDB:**

Sign up and log in to MongoDB Atlas.
  Create a new project and build a free-tier cluster.
  Create a database user with username and password.
  Connect to DB on MongoDB Compass.
  Obtain the connection string (MongoDB URI).
  Configuring the backend and connecting it with a MongoDB instance.

  Connect to the backend instance using SSH with the key pair.
  Clone the Repository: git clone https://github.com/munisekar-py/AWS-Cloud-Deployment.git
  Jump to Backend directory: cd TravelMemory/backend/
  Create .env to connect to DB: sudo vim  .env
  Enter Mongo DB URI: MONGO_URI='ENTER_YOUR_URL' PORT=3001
  in My case : **mongodb+srv://munisheak:r2V7267uMR1qUvRt@munish-travel-mem.sz1p7kc.mongodb.net/**
  Install Node.js: sudo apt install nodejs -y
  Install NPM Modules : sudo npm install
  Run Node.js application: sudo node index.js &

Backend Initial Testing with EC2 Public IP

![image](https://github.com/user-attachments/assets/a7db4657-7799-4f2e-87a5-986a9fbfa352)

Configuring frontend and linking it to the backend.

Connect to the frontend instance using SSH with the key pair.
Clone the Repository: git clone https://github.com/munisekar-py/AWS-Cloud-Deployment.git
Jump to Frontend directory: cd TravelMemory/frontend/
Create .env to connect to DB: sudo vim .env
Enter Backend public IP to link both: REACT_APP_BACKEND_URL=http://localhost:3001
Install packages: sudo npm install
Start application: sudo npm start

![image](https://github.com/user-attachments/assets/5d6bb094-713e-401f-bda3-3bf273004130)

**Implementing load balancing to divide traffic.**

Creat AMI template images for both the frontend and backend instances, then launch new instances from these templates.
Create Target groups for both backend and frontend instaces seperately.
Navigate to AWS Elastic Load Balancer (ELB) and select Create Load Balancer.
Attach the target groups to the Load Balancer listener on port 80.
Configure Health checks to ensure traffic only routes to healthy instances.
Verify the setup by accessing the ELB DNS name to confirm load-balanced access to the application.

![image](https://github.com/user-attachments/assets/5f91f09f-d032-4a64-b91b-a713b374cc3e)

![Screenshot from 2025-06-19 19-43-52](https://github.com/user-attachments/assets/c9a3a1de-7bfd-41d6-97ee-189a1a6ddfe8)

![Screenshot from 2025-06-19 21-16-15](https://github.com/user-attachments/assets/1e430b93-53f8-4348-b0b2-78a4d05689eb)

![Screenshot from 2025-06-19 22-05-33](https://github.com/user-attachments/assets/e3b82378-d1b7-4692-a573-f5e01ba8ddc9)

## **Configuring Reverse proxy on Front end to listen Port 80 **

![Screenshot from 2025-06-19 20-37-27](https://github.com/user-attachments/assets/3357a5d3-640e-4ba4-9f3b-1366476847c5)



**Integrating a custom domain using Cloudflare.**

Purchased the domain: munisekar.com from https://www.cloudflare.com/
Linked the domain with Cloudflare by updating cloudflair's nameservers to Cloudflare's.
Created a CNAME record for AWS ELB DNS name pointing to **http://travel.munisekar.com** in Cloudflare.
Created an SSL certificate using AWS Certificate Manager (ACM) and attached it to the Elastic Load Balancer to enable HTTPS via Cloudflare's SSL/TLS settings.

![image](https://github.com/user-attachments/assets/76617bb0-939c-4cd7-affa-9c326eddfddc)

![Screenshot from 2025-06-18 20-49-57](https://github.com/user-attachments/assets/4c3708c4-f4a3-46de-8795-ee873c1441f2)


## **Testing final results with **http://travel.munisekar.com** 

![Screenshot from 2025-06-19 21-46-30](https://github.com/user-attachments/assets/adc3a368-73a9-429f-a705-5d96a97c952f)

![Screenshot from 2025-06-19 22-03-20](https://github.com/user-attachments/assets/7f51f7c7-6f5d-4b54-b0f2-1955b0f04d9f)

![Screenshot from 2025-06-19 22-03-20](https://github.com/user-attachments/assets/8587b8c4-b60b-4e7c-b179-daca3a94c1d8)
![Screenshot from 2025-06-19 22-06-57](https://github.com/user-attachments/assets/ea698a2b-7cd0-4435-b500-8f0873d8e062)


Application executed as expected 
