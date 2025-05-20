# **BLOG App (API_Routing)**
![screenShort](https://github.com/mukeshvommu318/Featching_and_Routing_Part-3-NXT-/blob/49e7b57e8eba7006837a36a12b1be20ea5219559/Screenshot%20(5).png)

## Learnings
-> **Featching Data from API and Modifying the Data (Changing snake_case to camelCase)**

**code**


# **How to Deploy React Js Application into the GitHub** 
## Step 1: Create the GitHub repository
## Step 2: After Creating Repository Follow this Steps
    git init

    git add .

    git commit -m "first commit"

    git branch -M main
    
##  Step 3: Enter the following command in which we have to replace the <username> with the username of your GitHub account and the <rep Name> with the name of the repository which you have created.
    git remote add origin https://github.com/<username>/<rep Name>.git

## Enter the following commands which will push the react application to the above repository
    git push -u origin main

## Step 4 Adding the GitHub Pages dependency packages
    npm install gh-pages --save-dev

## Step 5 Adding the properties to the package.json file
    "homepage": "https://<Username>.github.io/<Repository-name>"
    
    "scripts":{
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build" 
    } 

## Step 6 Pushing the code updates to the GitHub repository and finally deploying the application
    git add .
    git commit -m "commit"
    git push

    npm run deploy

