# Deploying a Node Js Application on AWS EC2

### Set up an AWS EC2 instance

1. Create an IAM user & login to your AWS Console
    - Access Type - Password
    - Permissions - Admin

2. Create an EC2 instance
    - Select an OS image - Ubuntu
    - Create a new key pair & download `.pem` file
    - Instance type - t2.micro

3. Remove inherited permissions and grant read permissions to the current user
```
	icacls "nodejs.pem" /inheritance:r
	icacls "nodejs.pem" /grant:r "$($env:USERNAME):(R)"
```

4. Connecting to the instance using ssh
```
ssh -i instance.pem ubunutu@<IP_ADDRESS>
```

### Configuring Ubuntu on remote VM

1. Updating the outdated packages and dependencies
```
sudo apt update
```

2. Install Nodejs 
```
sudo apt install nodejs
```

3. Install npm
```
sudo apt install npm
```

### Deploying the project on AWS

1. Clone this project in the remote VM
```
git clone https://github.com/isaudkhan/Deploy-NodeJs-App-AWS-EC2.git
```

2. Setup the following environment variables - `(.env)` file
```
DOMAIN= "http://localhost:3000"
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```

3. Initialise and start the project
```
npm install
npm run start
```

### Project is deployed on AWS 🎉
