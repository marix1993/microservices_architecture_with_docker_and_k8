What is K8?
-

Kubernetes (also known as K8) is a container orchestration platform that automates many of the manual processes involved in deploying, managing, and scaling containerized applications.

## When not to use Microservices?

Microservices architecture is a great way to manage a large project, thanks to it flexibility and scalibility. However, it also requires a high maintanance and a high cost. So if your project is of a small scale and there is no plan of expanding and growing in the future, then it might be much simplier and more cost effective to use a Monolith or N-tier architecture instead.

## Benefits of K8:

- Reduced development and release time

- Optimizes cost

- Increased scalability and availability

- Flexibility in multi-cloud environments

- Cloud migration

K8 set up process:
-

1. Open Docker.
2. Go to Settings.
3. Select `Kubernetes` and then tick the box that says `Enable Kubernetes` and click on "Apply and Restart". 
It will take some time download and install Kubernetes.

After installation make sure to restart you machine.

To check if everything has been installed, in GitBash use `kubectl`.
To check if any of the services is running use: `kubectl get svc`

## Nginx deployment script:

1. First in your project folder crete a new YAML file, for example: `nginx-deployment.yml`
2. Write this code inside:
```commandline
apiVersion: apps/v1 # which api to use for deployment

kind: Deployment # what kind of service/object do you want to create?
# what would you like to call it - name of the service
metadata:
  name: nginx-deployment # naming deployment
spec:
  selector:
    matchLabels:
      app: nginx #look for this label to match with k8 service
  # Replica set 
  replicas: 3
  #template to use
  template:
    metadata:
      labels:
        app: nginx #this label connects to the service or any other k8 component

    # Container spec
    spec:
      containers:
      - name: nginx
        image: marix1993/tech221-nginx:v2 #use the image from Docker
        ports:
        - containerPort: 80 
```
3. `kubectl create -f nginx-deployment.yml` - use this command to create a service, where `-f` means file, and `nginx-deployment.yml` is the name of the YAML script.
4. You can use `kubectl get deploy` to check services deployed
5. `kubectl get pods` - shows you the status of pods
6. `kubectl delete deploy nginx-deployment` - to delete the service

## Creating an nginx service to connect to the port

1. Create a new YAML file called `nginx-service.yml`
2. Add the following script:

```commandline
# Select the type of API version and type of service/object
apiVersion: v1
kind: Service
# Metadata for name
metadata:
  name: nginx-svc
  namespace: default #sre

# Specification to include ports Selector
spec:
  ports:
  - nodePort: 30001 # range is 30000-32768
    port: 80

    targetPort: 80


  selector: 
    app: nginx # this label connectthis service to deployment

  type: NodePort 
```

3. Use `kubectl create -f nginx-service.yml` - to run service script
4. Use `kubectl get pods` to check if pods are running
5. Go to your `localhost:30001` in order to check if the page is working
6. You can use `kubectl delete pod <pod_id>` to delete the pod and check if "self-healing" works and if it automatically starts a new pod

## Create a node deployment pod.

1. In your project folder create a new YAML file, for example `node-deployment.yml`.

2. Write the following script:
```commandline
apiVersion: apps/v1 # which api to use for deployment

kind: Deployment # what kind of service/object do you want to create?
# what would you like to call it - name of the service
metadata:
  name: node-deployment # naming deployment
spec:
  selector:
    matchLabels:
      app: node #look for this label to match with k8 service
  # Replica set
  replicas: 3
  #template to use
  template:
    metadata:
      labels:
        app: node #this label connects to the service or any other k8 component

    # Container spec
    spec:
      containers:
      - name: node
        image: marix1993/sparta_app:v1 #use the image from Docker
        ports:
        - containerPort: 80
```
3. `kubectl create -f node-deployment.yml` - use this command to create a service, where -f means file, and node-deployment.yml is the name of the YAML script.
4. You can use `kubectl get deploy` to check services deployed
5. `kubectl get pods` - shows you the status of pods

## Create a service for node app to run on port 30002.

1. Create a new YAML file called `node-service.yml`
2. Add the following script:
```commandline
# Select the type of API version and type of service/object
apiVersion: v1
kind: Service
# Metadata for name
metadata:
  name: node-svc
  namespace: default #sre

# Specification to include ports Selector
spec:
  ports:
  - nodePort: 30002 # range is 30000-32768
    port: 3000

    targetPort: 3000


  selector: 
    app: node # this label connectthis service to deployment

  type: NodePort 
```

3. Use `kubectl create -f node-service.yml` - to run service script
4. Use `kubectl get pods` to check if pods are running
5. Go to your `localhost:30002` in order to check if the page is working

![300002.png](file%2F300002.png)
