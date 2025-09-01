<<<<<<< HEAD


## 🏗️ Project Architecture (Stepwise)

```
VS Code (Development)
   │
   ▼
Git (Commit/Push)
   │
   ▼
GitHub Repository (main / Prod branch)
   │
   ▼
Azure Portal
   │
   ├── Go to your Web App > Overview > Get Publish Profile (download)
   │
   ▼
GitHub (Repository Settings)
   │
   ├── Settings > Secrets and variables > Actions > New repository secret
   │
   ├── Add secret: AZURE_WEBAPP_PUBLISH_PROFILE (for main)
   │
   ├── Add secret: AZURE_WEBAPP_PUBLISH_PROFILE_PROD (for Prod)
   │
   ▼
GitHub Actions Workflow
   │
   ├── Uses: azure/webapps-deploy@v2
   │
   ├── app-name: ${{ env.AZURE_WEBAPP_NAME }}
   │
   ├── publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE }} (main)
   │
   ├── publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE_PROD }} (Prod)
   │
   └── package: ${{ env.AZURE_WEBAPP_PACKAGE_PATH }}
   │
   ▼
Azure Web App (Deployed)
=======


## 🏗️ Project Architecture (Stepwise)

```
VS Code (Development)
   │
   ▼
Git (Commit/Push)
   │
   ▼
GitHub Repository (main / Prod branch)
   │
   ▼
Azure Portal
   │
   ├── Go to your Web App > Overview > Get Publish Profile (download)
   │
   ▼
GitHub (Repository Settings)
   │
   ├── Settings > Secrets and variables > Actions > New repository secret
   │
   ├── Add secret: AZURE_WEBAPP_PUBLISH_PROFILE (for main)
   │
   ├── Add secret: AZURE_WEBAPP_PUBLISH_PROFILE_PROD (for Prod)
   │
   ▼
GitHub Actions Workflow
   │
   ├── Uses: azure/webapps-deploy@v2
   │
   ├── app-name: ${{ env.AZURE_WEBAPP_NAME }}
   │
   ├── publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE }} (main)
   │
   ├── publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE_PROD }} (Prod)
   │
   └── package: ${{ env.AZURE_WEBAPP_PACKAGE_PATH }}
   │
   ▼
Azure Web App (Deployed)
>>>>>>> 36d5879 (Updated index.html)
```