**AWS Management Console:**
   - Web-based interface for managing AWS services

**AWS Global Infrastructure:**
   - AWS global data center network

**Availability Zones:**
   - AWS data center clusters

**Amazon EC2 Instance Types:**
   - EC2 virtual machine configurations

**Storage and Database:**
   - Amazon S3: Object storage
   - Amazon RDS: Managed databases
   - Amazon DynamoDB: Managed NoSQL

# Docker Installation


### Quick Install
```bash
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```
---

installing packages:
```bash
sudo apt update
sudo apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    jq
```

Add Docker’s official GPG key:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

setup repository:
```bash
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Install Docker Engine:
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

Add your user to the docker group:
```bash
sudo usermod -aG docker $USER
```

### Docker Compose

download the current stable release of Docker Compose:
```bash
COMPOSE_VERSION=$(curl -s "https://api.github.com/repos/docker/compose/tags" | jq -r '.[0].name')
sudo curl -L "https://github.com/docker/compose/releases/download/${COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose
```

Get executable permissions to the binary:
```bash
sudo chmod +x /usr/local/bin/docker-compose
```

### Pull Docker Images
```bash
docker pull hello-world
````
```bash
docker pull nginx
````
```bash
docker pull ubuntu/apache2
````
### Listed Images
```bash
docker images
````
### Port Forwarding nginx
```bash
docker run --name mynginxl -p 80:80 -d nginx
````
### Killing nginx to run Apache2
```bash
docker kill mynginxl
````
### Port Forwaring Apache2
```bash
docker run --name myapache -p 80:80 -d ubuntu/apache2
````

# **Network Services**
- VPC : own insolated environment in a public cloud
- Domain Name Service - Route 53

  ![Screenshot 2023-12-04 095334](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/50172c88-8a89-4583-8600-3b26994aa235)

- public subnet : can receive traffic from outerworld 
- private subnet : cannot receive traffic from outerworld but may or may not send traffic to outerworld

  ![2](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/a066ae01-f823-4cd6-9d5d-ca9a99755d4f)

![3](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/30c9b03e-3c86-458c-8425-e168770f6068)

![4](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/8928a661-2386-4898-b331-0f83d5c82ec0)

- **Apache web server works on layer 7 , using single apache server one can deploy multiple applications on different ports based on paths (URLbased) (virtual hosts) . virtual hosting can only work on layer 7**

# **Application based LB** 
- key pair : kind of like a password (public key is username; private key is password)
  - PPK (PuTTY Private Key) and PEM (Privacy Enhanced Mail) are two file formats that are commonly used for SSH and SSL/TLS connections. While PPK files are primarily used with PuTTY on Windows, PEM files are more widely supported and can be used with various tools and platforms

- security groups : A security group controls the traffic that is allowed to reach and leave the resources that it is associated with. For example, after you associate a security group with an EC2 instance, it controls the inbound and outbound traffic for the instance. When you create a VPC, it comes with a default security group. (acts as a firewall)

# **Creating a target group**  

- Your load balancer routes requests to the targets in a target group and performs health checks on the targets.
- LB routes traffic to target group then traffic group routes traffic to the back end ec2 instances or IP addresses etc

  ![5](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/e04cbe0e-cd63-47b8-ab1b-190a139d1460)

![6](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/acd6fa10-d017-4359-8e23-7cd439cbc208)

![7](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/89b58503-ad42-4e58-89be-00f8ee08bec9)

# **AUTOSCALING**
   AWS Auto Scaling monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost. Using AWS Auto Scaling, it's easy to setup application scaling for multiple resources across multiple services in minutes.

+ **Creating launch template**

![8](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/09dea64e-7b69-4608-8f57-c236f5226e40)


![9](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/12a9d7de-bfbd-4b73-adfc-1b33086e99c0)

![10](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/5b94f88a-c315-4ad1-9182-7876ff0825de)

# **Creating Scalling policies**

![12](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/a90b7060-300d-4ec6-991f-289901dcaac9)

![13](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/18cb88db-7c03-4a0e-9473-a750d38392d6)

# **AWS CLI**
  The AWS Command Line Interface (AWS CLI) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

+ BOTO library in python

  ![14](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/bdab1c8b-0070-4c1f-b344-522782529ffc)

+ sudo snap install aws-cli
+ aws configure
+ in security credentials, before creating access key copy and paste PU, prk and fill location and format in terminal
+ give user access

![15](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/b13de8a4-506c-49f6-9626-e14374f2c72b)

+ after creating instances \
+ aws ec2 describe-instances

  ![16](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/dee95ffc-e88b-4765-9c5d-d387f8575296)

![17](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/4ce7c02b-5df1-411d-adcc-d2374261e587)

+ docker image to create art load
+ pods - Pods are the smallest deployable units of computing that you can create and maange in kubernets. A Pod is a group of one or more containers, with shared storage and network resources, and a specifications for how to run the containers
+ daemon sets - works on nodes where pods are running, can manage all your agents.

# **CLOUD-9**
+ cloud based IDE
+ provides IDE on browsers

  ![18](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/20094970-feed-41c7-ba30-5d05e8ed86c1)

![19](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/f3b0aec8-45f8-453e-afc8-7116b41cb6b0)
+ after configuring aws cli on cloud 9
+ configure EKS ctl and kubectl

  ![20](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/281e76ca-810a-4d62-a321-39e6e64c2fbb)

+ launching a cluster
eksctl create cluster --name test --version 1.28 --nodegroup-name ng.default --node-type t3.micro --nodes 2 --managed

  ![21](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/a796102b-caf0-4127-9cbb-4635128a7748)

+ yaml file for nginx container launched with official nginx inage

         apiVersion: apps/v1
      kind: Deployment
      metadata:
       labels:
        environment: test
       name: test
       spec:
       replicas: 1
       selector:
        matchLabels:
             environment: test
      template:
        metadata:
            labels:
                environment: test
        spec:
            containers:
            - image: nginx:1.16
              name: nginx

         nano nginx-deployment.yaml
  + kubectl is the thing using which we will be creating, launching the resources, creating pods, troubleshooting cluster using kubecti
  + we will apply this file using kubectl

            kubectl apply -f nginx-deployment.yaml

![22](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/a3af4d46-3c54-468d-90e7-4e62196bd886)

+ autoscaler used by eks

  ![23](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/3007bffe-af4d-47e6-ae03-9121906c6c94)

can scale it

![24](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/360e80ba-dda2-4892-9875-82e71482b2d0)

+ install matrix server , will continue to moniter the cpu matrix , without this will not show how much resources are utilised

      kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

  + creating php-apache autoscaling yaml file for horizontal pod autoscaling

          apiVersion: apps/v1
          kind: Deployment
         metadata:
            name: php-apache
         spec:
          selector:
             matchLabels:
                  run: php-apache
         template:
           metadata:
              labels:
        run: php-apache
               spec:
             containers:
                - name: php-apache
              image: registry.k8s.io/hpa-example
        ports:
        - containerPort: 80
        resources:
          limits:
            cpu: 500m
          requests:
            cpu: 200m
            ---
               apiVersion: v1
            kind: Service
           metadata:
                 name: php-apache
             labels:
                 run: php-apache
            spec:
            ports:
             - port: 80
               selector:
                 run: php-apache
---

              apiVersion: autoscaling/v1
             kind: HorizontalPodAutoscaler
                metadata:
                    name: php-apache
                     namespace: default
              spec:
                 scaleTargetRef:
     apiVersion: apps/v1
     kind: Deployment
     name: php-apache
            minReplicas: 1
             maxReplicas: 10
            targetCPUUtilizationPercentage: 50
    
    nano hpa.yaml

+ deploying

            kubectl apply -f hpa.yaml

  ![25](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/a682af01-2876-4bcc-b9b4-6b052e904604)
 + creating a load balancer type service

   ![26](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/96732d8e-da04-423a-b2de-cfa98ea74438)

+ creating nodeport service

  ![27](https://github.com/ManavCodingspace/AWS-PRACTICALS/assets/145857624/800db44c-dbab-49a1-b9aa-c70099912822)

# **EKS**
Amazon Elastic Kubernetes Service (Amazon EKS) is a managed Kubernetes service that makes it easy for you to run Kubernetes on AWS and on-premises. Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications.
