## What are Microservices?

![ms_diagram.png](file%2Fms_diagram.png)

- Microservices, in simple terms, is an architectural approach where a complex application is built as a collection of small, independent, and loosely coupled services. Each service focuses on performing a specific business function and operates as a separate and autonomous unit.


- Imagine a traditional monolithic application as a single large building where all the different functionalities are tightly integrated. In contrast, microservices are like smaller, individual houses that work together to form a neighborhood.


- In a microservices architecture, each service is responsible for a specific task, such as user authentication, data storage, or order processing. These services communicate with each other through well-defined APIs (Application Programming Interfaces). Each service can be developed, deployed, and scaled independently, using the most suitable technology or programming language for its specific purpose.

## Difference between N-tier Architecture and Microservices:

N-tier architecture and microservices architecture are two different approaches for building applications. Here are the key differences between the two:

1. Scope and Complexity:

- N-tier architecture typically refers to dividing an application into three layers: presentation, business logic, and data storage. It is a more traditional approach where the application is organized into distinct layers, but all the components within each layer are tightly coupled. 


- On the other hand, microservices architecture focuses on breaking down the application into a collection of small, independent services. Each microservice handles a specific business capability and can be developed, deployed, and scaled independently.


2. Communication: 

- In N-tier architecture, the communication between different layers typically occurs within the same application or through APIs. The layers communicate synchronously, often within the same process or server. 


- In microservices architecture, services communicate with each other through well-defined APIs, but the communication is typically asynchronous and happens over a network. Microservices often use lightweight protocols like HTTP or messaging systems for inter-service communication.


3. Scalability and Flexibility: 

- N-tier architecture often scales by adding more resources to each layer. For example, if there is increased demand on the presentation layer, more servers can be added. 


- Microservices architecture allows for independent scaling of individual services. Services can be scaled individually based on their specific needs, which provides more flexibility and efficient resource utilization.


4. Deployment and Development: 

- N-tier architecture typically involves deploying the entire application as a single unit. Updates and changes to one layer may require redeployment of the entire application. 


- In microservices architecture, each service can be developed, deployed, and updated independently. This allows for faster development cycles, easier maintenance, and the ability to adopt different technologies or programming languages for different services.


5. Complexity Management: 

- N-tier architecture tends to have simpler management and governance since it deals with a smaller number of components. 


- Microservices architecture introduces a higher level of complexity due to the larger number of services, inter-service communication, and management of distributed systems. It requires proper design, monitoring, and orchestration mechanisms to ensure effective coordination and scalability.

## What is Docker?

![docker_diagram.png](file%2Fdocker_diagram.png)

- Docker is a software platform that allows you to package, distribute, and run applications in a containerized environment.


- Think of a container as a lightweight, isolated package that contains everything an application needs to run, such as the code, runtime, system tools, and libraries. Docker provides tools and a runtime environment to create and manage these containers.

## What is Containerisation?

- Containerization is a method of packaging and running applications with their dependencies in a standardized and isolated environment called a container.


- Imagine a container as a self-contained box that holds everything an application needs to run, including the code, libraries, dependencies, and configurations. This container is separate from the underlying infrastructure, such as the operating system or hardware, and can run consistently across different computing environments.


- Containerization provides several benefits:

  - First, it ensures that an application runs the same way regardless of the host system, which eliminates compatibility issues. 
  - Second, it enables the efficient utilization of system resources by allowing multiple containers to run on a single machine, each with its own isolated environment. 
  - Third, containers offer lightweight and fast startup times, making application deployment and scaling more efficient.

## What is the difference between containerization and virtualization?

- Virtualization involves creating multiple virtual machines (VMs) on a physical server, where each VM runs its own complete operating system (OS) and has dedicated resources. It mimics the behavior of a physical server but allows for better resource utilization by running multiple VMs on a single physical machine. Each VM is isolated from other VMs and operates independently.


- On the other hand, containerization operates at a higher level of abstraction. Containers are lightweight and share the host OS kernel, eliminating the need for running a separate OS for each application. Multiple containers can run on the same host, and they are isolated from each other at the application level. Each container encapsulates the application and its dependencies, providing a portable and consistent environment for the application to run.






