To get started with SonarQube on GitHub, the most efficient path is to connect SonarQube Cloud (formerly SonarCloud) directly to your GitHub repository using GitHub Actions. This automates code quality and security scans every time you push code or open a pull request. [1, 2, 3]  
Here is the step-by-step guide to setting it up. 
1. Connect SonarQube to GitHub 

1. Go to the SonarQube Cloud Product Page and log in using your GitHub credentials. 
2. Install the SonarQube Cloud application to grant access to your GitHub organization or personal repository. 
3. Select the specific repository you want to analyze and click Set up. [1, 4]  

2. Configure GitHub Secrets 
You must authorize GitHub Actions to send analysis data to your SonarQube dashboard securely. 

1. Inside your SonarQube account, navigate to your account security settings and generate a Sonar Token. 
2. Open your repository on GitHub and go to Settings &gt; Secrets and variables &gt; Actions. 
3. Create a new repository secret with the name  and paste your generated token as the value. 
4. (Optional) If you are hosting your own server instead of the cloud version, add a secret named  containing your server link. [3, 5, 6, 7]  

3. Add the Configuration File 
Create a file named  in the root directory of your GitHub repository. This file tells the scanner how to process your codebase. Add the following content: [3, 5]  
(Replace  with the exact keys provided in your SonarQube project dashboard). [5, 8]

```properties
sonar.projectKey=your_organization_your_project_name
sonar.projectName=Your Project Name
sonar.sources=src
sonar.sourceEncoding=UTF-8
```

5. Create the GitHub Actions Workflow 
Create a new workflow file at  in your repository to trigger the automated scan. Use the Official SonarQube Scan Action by adding this code: [3, 7, 9]

```yaml
name: SonarQube Analysis

on:
  push:
    branches:
      - main
  pull_request:
    types: [opened, synchronize, reopened]

jobs:
  sonarqube:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Source Code
        uses: actions/checkout@v4
        with:
          fetch-depth: 0 # Required for better blame information

      - name: Run SonarQube Scan
        uses: sonarsource/sonarqube-scan-action@v3
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
          # SONAR_HOST_URL: ${{ secrets.SONAR_HOST_URL }} # Uncomment if using a self-hosted instance
```

7. Run and Verify 

1. Commit and push the new files to your  branch. 
2. Navigate to the Actions tab in your GitHub repository to see the pipeline run. 
3. Once completed, your code quality metrics, bugs, and security vulnerabilities will display instantly on your  SonarQube Dashboard . [1, 3, 5, 10, 11]  

If you would like, tell me: 

• What programming language or framework your project uses (e.g., Java, JavaScript/TypeScript, Python)? 
• Are you using the free SonarQube Cloud or hosting a self-hosted SonarQube Server? [12, 13]  

I can help you tailor the build setup to generate test coverage reports for your specific stack. 

AI responses may include mistakes.

[1] https://docs.sonarsource.com/sonarqube-cloud/getting-started/github
[2] https://docs.sonarsource.com/sonarqube-server/discovering/devops-platforms/github
[3] https://medium.com/@ui.sachin732/configure-github-repository-with-sonarqube-sonarcloud-b1095c4ef685
[4] https://www.youtube.com/watch?v=K1zaFcmkARo
[5] https://www.youtube.com/watch?v=CK0y_E47DGw
[6] https://docs.sonarsource.com/sonarqube-server/9.9/devops-platform-integration/github-integration
[7] https://docs.sonarsource.com/sonarqube-server/9.8/devops-platform-integration/github-integration
[8] https://github.com/SonarSource/sonarcloud-github-action/blob/master/README.md
[9] https://github.com/marketplace/actions/official-sonarqube-scan
[10] https://docs.sonarsource.com/sonarqube-server/10.6/devops-platform-integration/github-integration/adding-analysis-to-github-actions-workflow
[11] https://www.youtube.com/watch?v=AYl3A3ac7bg
[12] https://www.sonarsource.com/integrations/azure/
[13] https://github.com/SonarSource/getting-started-agentic-analysis-claude-code

