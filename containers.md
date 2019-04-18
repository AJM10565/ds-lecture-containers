<WIP> 
<TODO Reformat Sources to proper style>

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
A container provides operating system (OS)-level virtualization. In a standard computer system a given application is able to view information about it's host's resources, even if it is unauthorized to make any modifications. A container can be allocated a precise amount of resources, and will assume that these are all it ever has to work with (). 

Additionally, the environment of a container can be initialized completely separately from whatever host is providing resources. This means that a machine running inside a container can be running a completely different operating system from it's host, and may contain a different service bundle. What this also means is that since a container's environment is specified by the creator, a user can mock a production system by initializing the container environment to mimic that of the test case. This fundamentally changes the way integration testing can be done (). 

Historically containers were used to test software on linux machines by using chroot which allowed the user to change the root directory of the application so that if the application is unsafe, the side-effects produced are contained. (https://www.networkworld.com/article/2226996/software-containers--used-more-frequently-than-most-realize.html) There were frequent attempts to fix the security vulnerabilites of chroot, this is documented further in Y. Korff et.al.(Y. Korff, P. Hope, and B. Potter, Mastering FreeBSD and OpenBSD Security. O’Reilly, 2005.) 

More modern methods of containerization or container-like systems include Docker, Kubernetes, Singularity, Solaris, vkernel, WPAR, LXC, and Virtuozzo. In the sections that follow we will examine the first three in greater detail.

### Docker
built from images
### Kubernetes
More than an orchestration tool
### Singularity
Hi performance Computing HPC, built for this.

### Concluding Thoughts
Containerization allows from migration transparency.
### Sources

    

    
