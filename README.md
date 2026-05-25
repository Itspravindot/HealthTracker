exp1:initialise,add,commit:

mkdir git-practical
cd git-practical
git init
echo "Hello World" > file.txt
ls
git status
git add .
git commit -m "First commit"
git log

exp2:create repo and push local project

repeat exp1 
create new rep and copy link
git remote add origin https://github.com/username/repo-name.git
Step 8: Push code
git push -u origin main

exp3:create branch, modify and merge

mkdir branchdemo
cd branchdemo
git init

echo "Main Branch" > file.txt
git add .
git commit -m "Initial commit"

git branch branch1
git checkout branch1

echo "Changes from branch1" >> file.txt
git add .
git commit -m "Updated in branch1"

git checkout main
git branch branch2
git checkout branch2

git checkout main
git merge branch1
git merge branch2


exp4:create pull request and solve merge
git clone https://github.com/username/repo.git
cd repo

git checkout -b branch1

echo "Branch1 change" > test.txt
git add .
git commit -m "branch1 update"
git push origin branch1

git checkout main
git checkout -b branch2

echo "Branch2 change" > test.txt
git add .
git commit -m "branch2 update"
git push origin branch2

Create Pull Request
Open GitHub
Compare branch1 with main
Click Create Pull Request

Merge conflict
When merging branch2:
Git shows conflict like:
<<<<<<< HEAD
Branch1 change
=======
Branch2 change
>>>>>>> branch2

Step 8: Resolve conflict
Edit file manually:
Branch1 change
Branch2 change

git add .
git commit -m "Conflict resolved"

exp5:Configure a basic GitHub Actions workflow to automatically display a build
success message on every push.


Step 1: Create folder structure
.github/workflows/

Step 2: Create file
.github/workflows/main.yml

Step 3: Add workflow code

name: Simple Workflow

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Display Message
      run: echo "Build Successful"

Step 4: Push to GitHub
git add .
git commit -m "Added workflow"
git push

Step 5: Check Actions tab
Open GitHub repository
Click Actions
Workflow runs automatically


exp8:create docker and docker image

mkdir dockerapp
cd dockerapp

Create Simple HTML File
nano index.html

Add this:

<h1>Hello from Docker Container</h1>

Save file.

Create file:
nano Dockerfile(in bash  D capitl)

Add this code:

FROM nginx:latest

COPY index.html /usr/share/nginx/html/  (add this in dockerfile) 

docker build -t myapp .

docker build -t myapp .

Open browser
http://localhost:8080

exp9:use docker to compse 2 container

mkdir compose-demo
cd compose-demo

nano docker-compose.yml

Add Compose Code:
version: '3'

services:

  web:
    image: nginx
    ports:
      - "8080:80"

  db:
    image: mysql

    environment:
      MYSQL_ROOT_PASSWORD: root

sudo systemctl start docker

docker-compose up -d

docker ps


Open Browser

Open:

http://localhost:8080

Nginx welcome page appears.

STEP 7: Stop Containers
docker-compose down


exp10: Ansible Playbok

sudo apt update
sudo apt install ansible -y

mkdir ansible-demo
cd ansible-demo

nano install.yml

---
- hosts: localhost
  become: yes

  tasks:

    - name: Install Apache
      apt:
        name: apache2
        state: present

    - name: Start Apache Service
      service:
        name: apache2
        state: started


ansible-playbook install.yml

Verify Apache

Open browser:

http://localhost
