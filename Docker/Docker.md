# Docker Installation

Created: December 4, 2021 2:42 PM
Last Edited Time: December 7, 2021 5:06 PM
Type: DevOps

<aside>
💡 MAKE SURE YOU HAVE A TRUST WORTHY INTERNET CONNECTION

</aside>

---

# Installing Docker on Ubuntu:

*ّ If you want to try docker without installation, search "Play With Docker" and use a 3 hour lifespan docker shell, for free.

### preprocess:

First of all:

it can only be installed on these OS's:

To install Docker Engine, you need the 64-bit version of one of these Ubuntu versions:

- Ubuntu Impish 21.10
- Ubuntu Hirsute 21.04
- Ubuntu Focal 20.04 (LTS)
- Ubuntu Bionic 18.04 (LTS)

Docker Engine is supported on `x86_64` (or `amd64`), `armhf`, `arm64`, and `s390x` architectures.

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

_________________________________

## Install using the repository

1. Update the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:
    
    ```bash
     sudo apt-get update
    
    $ sudo apt-get install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
    ```
    
2. Add Docker’s official GPG key:
    
    ```bash
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg |\
    sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    ```
    
3. Use the following command to set up the **stable** repository. To add the **nightly** or **test** repository, add the word `nightly` or `test` (or both) after the word `stable` in the commands below. [Learn about **nightly** and **test** channels](https://docs.docker.com/engine/install/).
    
    ```bash
    $ echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```
    

________________________________

## Install Docker Engine

1. Update the `apt` package index, and install the *latest version* of Docker Engine and containerd, or go to the next step to install a specific version:

```bash
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

1. To install a specific version of Docker Engine, list the available versions in the repo, then select and install: 
    1. List the versions available in your repo:

```bash
$ apt-cache madison docker-ce
```

       b. Install a specific version using the version string from the second column, for   example, `5:18.09.1~3-0~ubuntu-xenial`.

```bash
$ sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```

1. Verify that Docker Engine is installed correctly by running the `hello-world` image.
    
    ```bash
    $ sudo docker run hello-world
    ```
    

---

# Some Tricks:

Tricks you can dock them better 🦴

- Getting rid of "exited" containers:
    
    ```bash
    docker rm $(docker ps -a -f status=exited -q)
    ```
    

- Running in interactive mode:
    
    ```bash
    docker run -it MyImage
    ```
    

- Use *-d* switch if you want to get back to your shell after running a container. Then use *attach* if you need to get into the container.

- Containers only live as long as a process in them is alive. If you need to keep them running, use *-t* switch.

- Type only first few characters of a container's name, docker will understand it.

- You can map any port to your containers like this:
    
    ```bash
    docker run *num1*:*num2 MyImage* 
    ```
    
    *  *num1* is your internal port which other containers interact with your container inside docker and *num2* is the external port that other application out of docker, will use this port to connect with your container.
    
- By deleting a container, all the data that was created by that container, will also be erased. If you don't want that to happen, you can map your container directories to some directories out of docker host. Use this command:
    
    ```bash
    docker run *external_directory_address*:*internal_directory_address* MyImage
    ```
    

- Want more details on a container ?
    
    ```bash
    docker inspects MyContainr
    ```
    
    also you can use $(docker ps -a) and get details of all containers with all states.
    
- When writing a Dockerfile, there is two part, first word of all sentences are in CAPITAL and other words are small letters. The first group is called "instruction", you can google them always.
    - You can declare environmental variables in your apps and codes, then value them while writing the Dockerfile.
    - you can build your images using this command:
        
        ```bash
        docker build Dockerfile -t *dockerfile_address*
        ```
        

- You can limit the amount of resource a container uses, with this switchs:
    
    ```bash
    docker run —cpu=0.5 —memory=100m MyImage
    ```
    
    *0.5* here means %50. You also can do this resource management more precisely with container management tools like Kubernetes , Docker Swarm and ...