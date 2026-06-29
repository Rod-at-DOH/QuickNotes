## To access SonarQube using GitHub login, you need to register SonarQube as a GitHub App and configure the necessary settings for authentication.

### Steps to Set Up GitHub Authentication for SonarQube

1. **Register SonarQube as a GitHub App:**
- Go to your GitHub account and create a new GitHub App. This is essential for allowing users to log in with their GitHub credentials.
- Set the **Homepage URL** to the public URL of your SonarQube server (e.g., https://sonarqube.mycompany.com).
- Set the **Callback URL** to the same public URL of your SonarQube server.
- Deactivate the **Webhooks** feature for this app 

sonarsource.com

2. **Configure SonarQube Settings:**

- In SonarQube, navigate to **Administration > General > Server base URL** and ensure it matches the public URL you set in the GitHub App.
- Go to **Administration > Configuration > General Settings > Authentication > GitHub Authentication** and enable it. Enter the **Client ID** and **Client Secret** from your GitHub App 

3. **Login Process:**

- Once the setup is complete, users can log in to SonarQube by clicking the **Log in with GitHub** button on the SonarQube login page.
- After clicking the button, users will be redirected to GitHub to authenticate and authorize access to their account 

4. **User and Permission Management:**

- With GitHub authentication, user and group permissions can be automatically synchronized from GitHub to SonarQube. This means that any changes in GitHub regarding user roles will reflect in SonarQube 

5. **Additional Configuration:**
- You can customize permission mappings and enable project visibility synchronization to match GitHub repository settings with SonarQube project visibility 
- By following these steps, you can successfully set up and access SonarQube using GitHub login credentials, allowing for a seamless integration between the two platforms. For more detailed instructions, refer to the official SonarQube documentation.
