## Step 1: Create EC2 Instance
# Access Webiste
<img width="1364" height="678" alt="website access page" src="https://github.com/user-attachments/assets/7e5e355c-d4e9-4623-9e5f-842d10adf14a" />

IAM user with **access keys and secret access keys**
 <img width="1365" height="680" alt="iam role pic" src="https://github.com/user-attachments/assets/2c4f6eda-3412-4665-b005-288f3c0fa84f" />

 ## Step 2: Install ```AWS CLI```, ```Kubectl```, ```EKSCTL```:
 ```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

apt install unzip

unzip awscliv2.zip
```
- ```Kubectl``` - kubectl is the command-line tool used to interact with Kubernetes clusters.
```
curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.30.2/2024-07-12/bin/linux/amd64/kubectl

chmod +x kubectl

mv kubectl /usr/local/bin/kubectl
```    
- ```EKSCTL``` - eksctl is a command-line tool for managing Amazon EKS (Elastic Kubernetes Service) clusters.
```
curl -LO "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_Linux_amd64.tar.gz"

tar -xzf eksctl_Linux_amd64.tar.gz

sudo mv eksctl /usr/local/bin/

eksctl version
```
## Step 3: AWS Configure - 
        ○ Access Key - Your_Access_Key
        ○ Access Secret Key - Your Access_secret_key
        
## Step 4: Create EKS Cluster
```
eksctl create cluster --name flask-cloudwatch-project --region us-west-1 --node-type t3.micro --nodes-min 1 --nodes-max 2
```
## Step 5: Configure EKS Cluster
```
eksctl  create cluster --name flask-cloudwatch-project --region us-west-1
```

```
aws eks update-kubeconfig --name flask-cloudwatch-project --region us-west-1
```
<img width="1365" height="673" alt="eks project" src="https://github.com/user-attachments/assets/235e0a94-c8a7-48ab-97cf-865bdbaf2e71" />

## Step 6: Docker Installation 

```
sudo apt install docker.io -y
```

## Step 7: Give Permission Docker 

```
sudo usermod -aG docker $USER
sudo chmod 777 /var/run/docker.sock
```

## Step 8: Jenkins Installation

```
sudo apt update
sudo apt install fontconfig openjdk-21-jre
java -version
```

```
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```
<img width="1362" height="676" alt="cicd pipeline" src="https://github.com/user-attachments/assets/dd8c2808-86a2-4535-bae4-65a09996b528" />
<img width="1365" height="689" alt="docker credential" src="https://github.com/user-attachments/assets/756a3dc9-8426-4259-bac2-d6c70c9dd6ac" />
<img width="1365" height="197" alt="container running pic" src="https://github.com/user-attachments/assets/238b24d7-51db-4316-a8cc-4cbfecab21ce" />


## Step 8: Cloudwatch for Monitoring
```
curl https://raw.githubusercontent.com/aws-samples/amazon-cloudwatch-container-insights/main/k8s-quickstart/cwagent-custom-resource-definitions.yaml | kubectl apply --server-side -f -
```

```
curl https://raw.githubusercontent.com/aws-samples/amazon-cloudwatch-container-insights/main/k8s-quickstart/cwagent-operator-rendered.yaml | sed 's/{{cluster_name}}/'${ClusterName}'/g;s/{{region_name}}/'${RegionName}'/g' | kubectl apply -f -
```
<img width="1365" height="673" alt="cloudwatch pic 1" src="https://github.com/user-attachments/assets/466b45d7-882b-4866-93f1-1bca749ac86e" />
<img width="1365" height="571" alt="cloudwatch pic 2" src="https://github.com/user-attachments/assets/89fbbb2a-e94d-4539-ad31-896b50613928" />
<img width="1365" height="641" alt="cloudwatch pic 3" src="https://github.com/user-attachments/assets/4cdc7b6e-e659-49dc-9b94-59d25207c4b4" />






        

