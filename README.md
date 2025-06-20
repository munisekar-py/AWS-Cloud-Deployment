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
