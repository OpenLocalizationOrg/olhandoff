MS-TEST:::ms.ContentId: 526e4f1a-2936-4c61-b3be-d41b4cf9d10f
title: About Windows Server Containers

#MS-TEST:::Windows Server Containers

MS-TEST:::Test updates for demo tomorrow!
MS-TEST:::Applications fuel innovation in the cloud and mobile era.
MS-TEST:::Containers, and the ecosystem that is developing around them, will empower software developers to create the next generation of applications experiences.

MS-TEST:::Watch a short overview: [Windows-based containers: Modern app development with enterprise-grade control](https://youtu.be/Ryx3o0rD5lY).

##MS-TEST:::What are containers?

MS-TEST:::They are an isolated, resource controlled, and portable operating environment.

MS-TEST:::Basically, a container is an isolated place where an application can run without affecting the rest of the system and without the system affecting the application.
MS-TEST:::Containers are the next evolution in virtualization.

MS-TEST:::If you were inside a container, it would look very much like you were inside a freshly installed physical computer or a virtual machine.
MS-TEST:::And, to [Docker](https://www.docker.com/), a Windows Server Container can be managed in the same way as any other container.

##MS-TEST:::Container Fundamentals

MS-TEST:::When you begin working with containers you will notice many similarities between a container and a virtual machine.
MS-TEST:::A container runs an operating system, has a file system and can be accessed over a network just as if it was a physical or virtual computer system.
MS-TEST:::That said, the technology and concepts behind containers are very different from that of virtual machines.
MS-TEST:::[This blog post](http://azure.microsoft.com/blog/2015/08/17/containers-docker-windows-and-trends/) by Mark Russinovich explains containers well.

MS-TEST:::The following key concepts will be helpful as you begin creating and working with Windows Server Containers.

MS-TEST:::**Container Host:** Physical or Virtual computer system configured with the Windows Server Container feature.
MS-TEST:::The container host will run one or more Windows Server Containers.

MS-TEST:::**Container Image:** As modifications are made to a containers file system or registry, such as with software installation they are captured in the sandbox.
MS-TEST:::In many cases you may want to capture this state such that new containers can be created that inherit these changes.
MS-TEST:::That’s what an image is – once the container has stopped you can either discard that sandbox or you can convert it into a new container image.
MS-TEST:::For example, let’s imagine that you have deployed a container from the Windows Server Core OS image.
MS-TEST:::You then install MySQL into this container.
MS-TEST:::Creating a new image from this container would act as a deployable version of the container.
MS-TEST:::This image would only contain the changes made (MySQL), however would work as a layer on top of the Container OS Image.

MS-TEST:::**Sandbox:** Once a container has been started, all write actions such as file system modifications, registry modifications or software installations are captured in this ‘sandbox’ layer.

MS-TEST:::**Container OS Image:** Containers are deployed from images.
MS-TEST:::The container OS image is the first layer in potentially many image layers that make up a container.
MS-TEST:::This image provides the operating system environment.
MS-TEST:::A Container OS Image is Immutable, it cannot be modified.

MS-TEST:::**Container Repository:** Each time a container image is created the container image and its dependencies are stored in a local repository.
MS-TEST:::These images can be reused many times on the container host.
MS-TEST:::The container images can also be stored in a public or private repository such as DockerHub so that they can be used across many different container host.

MS-TEST:::**Container Management Technology:** Windows Server Containers can be managed using both PowerShell and Docker.
MS-TEST:::With either one of these tools you can create new containers, container images as well as manage the container lifecycle.

MS-TEST:::<center>![](media/containerfund.png)</center>

##MS-TEST:::Containers for Developers

MS-TEST:::From a developer’s desktop to a testing machine to a set of production machines, a Docker image can be created that will deploy identically across any environment in seconds.
MS-TEST:::This story has created a massive and growing ecosystem of applications packaged in Docker containers, with DockerHub, the public containerized-application registry that Docker maintains, currently publishing more than 180,000 applications in the public community repository.

MS-TEST:::When you containerize an app, only the app and the components needed to run the app are combined into an "image".
MS-TEST:::Containers are then created from this image as you need them.
MS-TEST:::You can also use an image as a baseline to create another image, making image creation even faster.
MS-TEST:::Multiple containers can share the same image, which means containers start very quickly and use fewer resources.
MS-TEST:::For example, you can use containers to spin up light-weight and portable app components – or ‘micro-services’ – for distributed apps and quickly scale each service separately.

MS-TEST:::Because the container has everything it needs to run your application, they are very portable and can run on any machine that is running Windows Server 2016.
MS-TEST:::You can create and test containers locally, then deploy that same container image to your company's private cloud, public cloud or service provider.
MS-TEST:::The natural agility of Containers supports modern app development patterns in large scale, virtualized and cloud environments.

MS-TEST:::With containers, developers can build an app in any language.
MS-TEST:::These apps are completely portable and can run anywhere - laptop, desktop, server, private cloud, public cloud or service provider - without any code changes.

MS-TEST:::Containers helps developers build and ship higher-quality applications, faster.

##MS-TEST:::Containers for IT Professionals

MS-TEST:::IT Professionals can use containers to provide standardized environments for their development, QA, and production teams.
MS-TEST:::They no longer have to worry about complex installation and configuration steps.
MS-TEST:::By using containers, systems administrators abstract away differences in OS installations and underlying infrastructure.

MS-TEST:::Containers help admins create an infrastructure that is simpler to update and maintain.

##MS-TEST:::Video Overview

<iframe src="https://channel9.msdn.com/Blogs/containers/Containers-101-with-Microsoft-and-Docker/player" width="960" height="540" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##MS-TEST:::Try Windows Server Containers

MS-TEST:::[Get started with Windows Server Containers in Windows Azure](../quick_start/azure_setup.md)  
[Get started with Windows Server Containers Locally](../quick_start/container_setup.md)

-------------------

MS-TEST:::
[Back to Container Home](../containers_welcome.md)




