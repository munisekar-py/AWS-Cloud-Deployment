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

Implementing load balancing to divide traffic.

Creat AMI template images for both the frontend and backend instances, then launch new instances from these templates.
Create Target groups for both backend and frontend instaces seperately.
Navigate to AWS Elastic Load Balancer (ELB) and select Create Load Balancer.
Attach the target groups to the Load Balancer listener on port 80.
Configure Health checks to ensure traffic only routes to healthy instances.
Verify the setup by accessing the ELB DNS name to confirm load-balanced access to the application.


 ** *********************************************************************************** **
 **               +--------------------------------------------+                        **
 **               |         Application Load Balancer          |                        **
 **               |                (Port 80)                   |                        **
 **               +--------------------------------------------+                        ** 
 **                       |                          |                                  **
 **              +--------+--------+         +-------+--------+                         **
 **              |                 |         |                |                         **
 **  Path: / or Host: frontend.*   |         |  Path: /api/*  |                         **
 **              |                 |         |                |                         **
 **  Target Group: Frontend-TG     |         |  Target Group: Backend-TG                **
 **              |                 |         |                |                         **
 **       +------+-----+           |     +---+------+          |                        ** 
 **       |            |           |     |          |          |                        **
**  +----------------+ +----------------+ +----------------+ +----------------+         **
**  | Frontend EC2-1 | | Frontend EC2-2 | | Backend EC2-1 | | Backend EC2-2 |           **
**  +----------------+ +----------------+ +----------------+ +----------------+         **
**        ↑                  ↑                 ↑                 ↑                      **
**        |   (Launched from Frontend AMI)     |  (Launched from Backend AMI)           **
**        +------------------------------------+-------------------------------+        **
**                           Health Checks on / & /api/ respectively                    ** 
**                                                                                      **
**  Access via:                                                                         **
**   → http://<ALB-DNS-Name>   → Load Balanced to Frontend or Backend                   **
**                                                                                      **    
**  *********************************************************************************** **
