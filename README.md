# Pushing the repo to Github and personalizing it
Did a git clone from the repo we are cloning from to my local
cd into the cloned repository 
git checkout -b prod --- this is to create a new branch where we want our work to be pushed into
delete the .git directory in our repo using "rm -rf .git"
run "git init" this it to create a new .git directory 
edit the pom.xml and the index.html file to add the lines of code needed and remove the ones not needed 
git commit -m "commit message"
ran "git remote add (repoURL that we are pushing to)" this is to add our own 
git remote -v --- this is to verify where our codes will be pushed to
ran git push aliasname(origin) prod to push to our github repository
# Build Project Using Maven

Maven is java based build tool to generate executable 

packages(jar, ear,war) for java based projects.

```bash
mvn clean package
```

## Create Docker Image
Docker is a continerization tool.Using docker we can deploy our applications as 

containers using docker images. Containers contains application code and also the softwares,

config files whatever is required for our application to run.

Create docker image using Dockerfile


```docker
docker build -t mylandmarktech/springapp .
```

## Deploy Application Using Docker Compose 

```docker-compose 
docker-compose up -d 
```

## List Docker Containers
```docker
docker ps -a
```
## License
[Landmark Technologies](http://www.mylandmarktech.com)
