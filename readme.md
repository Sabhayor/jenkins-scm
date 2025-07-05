\# Creating a Jenkins Freestyle Project



\### Step 1: Create a New Freestyle Project

1\. From the Jenkins \*\*dashboard menu\*\* on the left side, click on \*\*"New Item"\*\*.

2\. Enter the name \*\*`my-first-job`\*\*.

!\[Free style project](./images/free\_style\_project.png)

3\. Select \*\*"Freestyle project"\*\*.

4\. Click \*\*"OK"\*\* to proceed.



---



\# Connecting Jenkins to Our Source Code Management



\### Step 1: Create a GitHub Repository

\- Go to GitHub and create a new repository named \*\*`jenkins-scm`\*\*.

\- Ensure you add a \*\*README.md\*\* file during setup.



\### Step 2: Connect Jenkins to GitHub Repository

1\. Go back to Jenkins and open the \*\*`my-first-job`\*\* project.

2\. Click \*\*"Configure"\*\*.

3\. In the \*\*Source Code Management\*\* section:

&nbsp;  - Select \*\*Git\*\*.

&nbsp;  - Paste the \*\*repository URL\*\* (make sure the branch is set to `main`).



\### Step 3: Save and Build

\- Click \*\*"Save"\*\*.

\- Click \*\*"Build Now"\*\* to trigger the initial build and connect Jenkins to your repository.



!\[Build](./images/build.png)

---



\# Configuring Build Trigger



\### Step 1: Enable Build Trigger

1\. Open the \*\*`my-first-job`\*\* project and click \*\*"Configure"\*\*.

2\. Scroll to \*\*"Build Triggers"\*\* and check:

&nbsp;  - \*\*"GitHub hook trigger for GITScm polling"\*\*.

!\[Trigger](./images/configure\_trigger.png)



\### Step 2: Create GitHub Webhook

1\. Go to your \*\*GitHub repository settings\*\*.

2\. Under \*\*Webhooks\*\*, click \*\*"Add webhook"\*\*.

3\. In the \*\*Payload URL\*\*, enter your Jenkins server's IP and port in the following format:  

```



http://<your-jenkins-ip>:<port>/github-webhook/



```

4\. Choose \*\*application/json\*\* as the content type.

5\. Click \*\*"Add webhook"\*\* to save.



Now, whenever you push changes to your GitHub repository, Jenkins will automatically trigger a new build.



\## Error Encounterred

Inability to push/pull from github - This happened because my  local repo and my git repo had different roots. They were initialized separately and didn’t share a common history. The readme files were different.



!\[Pull error](./images/push\_error.png)

!\[Pull error](./images/pull\_error.png)



To resolve this, force Git to allow the merge by adding the --allow-unrelated-histories flag:

```

git pull origin main --allow-unrelated-histories

```



