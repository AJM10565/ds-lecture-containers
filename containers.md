<WIP> 
<TODO Reformat Sources to proper style>
<Progress was made>

 # Containers: Dockers, Kubernetes, Singularity #

 ### Containers Chapter Outline

- Introduction to Containers
    
- Discuss various Technologies
    - Docker
        - Overview of Docker
        - Explanation of key ideas in Docker
        - Example of how to use Docker
    - Kubernetes
        - Overview of Kubernetes
        - Explanation of key ideas in Kubernetes
        - Example of how to use Kubernetes
    - Singularity
        - Overview of Singularity
        - Explanation of key ideas in Singularity
        - Example of how to use Singularity
- Concluding thoughts
    - Usefulness
    - Review Relevant DS Principles
    - Discuss how containers Embody these principles
    - Practical Take-Aways for users
    
###Introduction to Containers
#### What are Containers?
A container provides operating system (OS)-level virtualization. In a standard computer system a given application is able to view information about it's host's resources, even if it is unauthorized to make any modifications. A container can be allocated a precise amount of resources, and will assume that these are all it ever has to work with (George Coulouris, Jean Dollimore, Tim Kindberg, and Gordon Blair. 2011. Distributed Systems: Concepts and Design (5th ed.). Addison-Wesley Publishing Company, , USA. CHAPTER 7). 

Additionally, the environment of a container can be initialized completely separately from whatever host is providing resources. This means that a machine running inside a container can be running a completely different operating system from it's host, and may contain a different service bundle. What this also means is that since a container's environment is specified by the creator, a user can mock a production system by initializing the container environment to mimic that of the test case. This fundamentally changes the way integration testing can be done . 
Containers should be considered as stand-alone application packages. They contain all required dependency information, and run on a thin layer above the host operating system with access to kernel methods. In addition to dependencies, containers can include files, environment variables, and software code. A particular application might consist of many individual containers that work in tandem to execute tasks. Sometimes the 'master' and 'worker' model is used, other times more complex systems are required. Multiple containers for the same application can run concurrently, and if one were to fail the others are able to re-load balance to accomodate new requests in a way seemless to the user experience. Similar to the JVM containers will run equally well on all host systems provided the host has access to the thin application layer that handles communication between the kernel and individual containers. Containers also play well with micro-services such that an individual service might be encapsulated inside a container, and at peak times more containers could be started-up and decommisioned when unnecessary.
#### A brief history of containers
Historically containers were used to test software on linux machines by using chroot which allowed the user to change the root directory of the application so that if the application is unsafe, the side-effects produced are contained. (https://www.networkworld.com/article/2226996/software-containers--used-more-frequently-than-most-realize.html) There were frequent attempts to fix the security vulnerabilites of chroot, this is documented further in Y. Korff et.al.(Y. Korff, P. Hope, and B. Potter, Mastering FreeBSD and OpenBSD Security. O’Reilly, 2005.) 

More modern methods of containerization or container-like systems include Docker, Kubernetes, Singularity, Solaris, vkernel, WPAR, LXC, and Virtuozzo. These systems rely on similar properties as chroot but were built to be more robust and provide a richer feature set.
#### Container Design Patterns
Any discussion of containers would be remiss if it did not discuss the  fundamental design patterns specific to this use case. These patterns are generally hard to specify correctly, and a good container provider will provide an interface to allow users to easily manage the problems solved by these patterns. These patterns include the following:
1. Leader election pattern\
    Deals with choosing a 'leader' container. Generally multiple leader containers are pre-built so that load can be balanced amongst available memebers at run-time. 
2. Work queue pattern\
   A work request is made, and so long as the containers are able to perform run() and mount() operations the work queue can be generated and maintained in a language agnostic way.

3. Scatter/gather pattern\
    Describes a system of minimally 2 containers. The first container is a leaf-type container, and the second is a parent container. The parent sends an information request to all leaves, each leaf responds with a partial view of the requested information (generally limited by their access), and the parent is responsible for collating and building a complete picture.

A more in-depth discussion of design patterns is beyond the scope of this chapter, but fundamentally these design principles govern how containers act in ensemble to solve problems.
(BURNS, B., AND OPPENHEIMER, D. Design patterns for
 container-based distributed systems. In Proceedings of the 8th
 USENIX Workshop on Hot Topics in Cloud Computing (HotCloud 16) (2016).)


### Docker
#### Overview of Docker
Docker was released in december of 2013. Docker is a service that provides  OS-level virtualization through the use of the docker daemon. Containers can be run in a number of different configuration types. Docker provides an CLI for user testing and access to the daemon. Individual Docker containers are built from Dockerfiles. Dockerfiles specify the environment, and other execution context for the application. An individual docker container can provide access to virtual ports and other networking tools. This makes Docker a useful container for doing integration testing. 

#### Explanation of key ideas in Docker
Docker containers are built from image files called Dockerfiles. Image files can be orchestrated in a docker swarm environment or fed into other orchestration tools. 


#### Example of how to use Docker
The docker documentation is user-friendly and easily explains how to make simple images.

    # Comment
    INSTRUCTION arguments
A sample image DOckerfile might look like the following:

    # Use an official Java runtime as a parent image
    FROM openjdk:8
    
    # Set the working directory to /app
    WORKDIR /app
    
    # Copy the current directory contents into the container at /app
    COPY . /app
    
    # Run bash script
    
    RUN git config --global url.”https://{<numbersequence>}:@github.com/".insteadOf “https://github.com/"
    
    RUN git clone https://github.com/user/project/
    
    RUN mvn install
    
    RUN java -Djava.net.preferIPv4Stack=true -jar path/to/your/jar/code
In the first line we specify a runtime language, and then we grab a project from github, build the project, and then execute a jar file. The container will now run as if it were inside a commandline, even thought it is running inside a container. Interactions with the container using the docker command line interface are identical to interactions as if the container was running in the host OS. Dockerfiles are executed sequentially from the top of the file. Instructions of type RUN are equivalent to command line instruction except these are run on the container OS. 


### Kubernetes
Kubernetes was released by Google in 2015. Kubernetes is well know for being an orchestration tool. This means that it is involved with load balancing and implements design patterns similar to Leader Election and Work queue. Less well known is that kubernetes also supports operations independent of other container software.
### Singularity
The HPC community was unhappy with the ability of technologies like docker and kubernetes to handle the massive loads of scientific computing, and so set out to build their own system for hosting containers on computing clustsers. This technology was released in 2017 for public use. Many national laboratories use Singularity to separate the concerns of their research from their computing hardware. This allows scientific computation to be cluster agnostic, and for research to be reproducible.

### Concluding Thoughts
Containerization allows from migration transparency.
### Sources

    

    
