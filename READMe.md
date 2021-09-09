# Automation with Jenkins
![](img/diagram1.png)
## Step 1: Have the instances ready (app and db)
## Step 2: Setup SSH key on the repo
### 2.1: Generate SSH key on local system
### 2.2: Deploy the key on the GitHub repo
## Step 3: Create webhook on github
## Step 4: Create jobs on Jenkins
### 4.1: **Test**
4.1.1 Select 'GitHub project' under 'General' and add the repo for the Project URL: https://github.com/ViMitre/sre_jenkins.git/<br>
4.1.2 Under Office 365 Connector, select 'Restrict where this project can be run' and add `sparta-ubuntu-node` for Label Expression<br>
4.1.3 Under 'Source Code Management' select 'Git', add the SSH address of the repo: `git@github.com:ViMitre/sre_jenkins.git`<br>
For credentials, add the private key generated for Jenkins<br>
4.1.4 Under 'Build Triggers', select `GitHub hook trigger for GITScm polling`
4.1.5 Add the following settings under 'Build Environment':
![](img/build_env.png)
4.1.6 Under '**Build**', add a build step and select '**Execute shell**' <br>
Add the following commands:
```
cd app
npm install
npm test
```
### **Once the second job is ready:**
Add a post-build action and select **'Build other projects'**, for projects to build add the next job.

### 4.2: **Github**
### 4.3: **Deploy**