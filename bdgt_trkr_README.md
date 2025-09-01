# Azure Budget Tracker

A comprehensive budget tracking application built with Python Flask, integrated with Azure services, and deployed using GitHub Actions.

## 🏗️ Architecture Overview

This project demonstrates a complete cloud-native application with the following components:

### **Backend Technologies**
- **Python Flask** - Web framework
- **Azure SQL Server** - Primary database
- **Azure Fabric** - Data analytics and reporting
- **Azure Web App Services** - Hosting platform

### **DevOps & CI/CD**
- **GitHub Actions** - Automated deployment pipeline
- **GitHub Branches** - Developer and Production workflows
- **Azure DevOps** - Integration with Azure services

### **Frontend**
- **Bootstrap 5** - Responsive UI framework
- **Chart.js** - Data visualization
- **Vanilla JavaScript** - Client-side functionality

## 🚀 Features

- ✅ **Transaction Management** - Add, view, and categorize income/expenses
- ✅ **Budget Tracking** - Set and monitor category-wise spending limits
- ✅ **Real-time Dashboard** - Live updates with spending analytics
- ✅ **Azure SQL Integration** - Secure cloud database storage
- ✅ **Automated Deployment** - CI/CD pipeline with GitHub Actions
- ✅ **Health Monitoring** - System status and database connectivity checks
- ✅ **Responsive Design** - Works on desktop and mobile devices

## 🔧 Setup Instructions

### Prerequisites
- Python 3.11+
- Azure Account with SQL Database
- GitHub Account (for Actions)
- VS Code or preferred IDE

### Local Development Setup

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd azure-budget-tracker
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   # Windows
   venv\Scripts\activate
   # macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   Create a `.env` file in the root directory:
   ```env
   AZURE_SQL_SERVER=your-server.database.windows.net
   AZURE_SQL_DATABASE=budget_tracker_db
   AZURE_SQL_USERNAME=your_username
   AZURE_SQL_PASSWORD=your_password
   FLASK_ENV=development
   ```

5. **Initialize the database**
   ```bash
   python database/azure_sql_setup.py
   ```

6. **Run the application**
   ```bash
   python app/main.py
   ```

## 🔀 GitHub Workflow

### Branch Strategy
- **`main`** - Production environment
- **`develop`** - Development environment
- **`feature/*`** - Feature development branches

### Git Commands Reference
```bash
# Create and switch to develop branch
git checkout -b develop

# Add changes
git add .
git commit -m "Add new feature"

# Push to GitHub
git push origin develop

# Merge to main (production)
git checkout main
git merge develop
git push origin main

# Go back to previous commit
git log --oneline
git checkout <commit-hash>

# Delete branch
git branch -d feature-name
git push origin --delete feature-name
```

## ☁️ Azure Services Integration

### Azure SQL Server Setup
1. Create Azure SQL Database
2. Configure firewall rules
3. Run setup scripts from `database/azure_sql_setup.py`

### Azure Web App Services
1. Create Web App in Azure Portal
2. Configure Python runtime
3. Set environment variables
4. Deploy using GitHub Actions

### Azure Fabric Integration
- Connect to SQL Database for analytics
- Create Power BI reports
- Set up data pipelines for ETL

## 🚀 GitHub Actions Deployment

### Required Secrets
Add these to your GitHub repository secrets:
- `AZURE_WEBAPP_PUBLISH_PROFILE_DEV` - Development environment
- `AZURE_WEBAPP_PUBLISH_PROFILE_PROD` - Production environment

### Deployment Workflow
1. **Development**: Push to `develop` branch → Auto-deploy to dev environment
2. **Production**: Push to `main` branch → Auto-deploy to production
3. **Quality Gates**: Automated testing, linting, and security scans

## 💰 Cost Optimization

### Azure Services (Low Budget)
- **Azure SQL Database**: Basic tier (~$5/month)
- **Azure Web App**: Free or Basic plan (~$10/month)
- **Azure Fabric**: Pay-per-use model

### GitHub Subscriptions
- **GitHub Pro**: $4/month per user
- **GitHub Actions**: 2,000 minutes/month free, then $0.008/minute
- **Developer Support**: Varies by plan

## 📊 Budget Tracking Features

The application tracks:
- Monthly income and expenses
- Category-wise spending limits
- Real-time budget alerts
- Visual spending analytics
- Transaction history

## 🔒 Security Features

- Azure SQL Server encryption
- Environment variable protection
- CORS configuration
- Input validation and sanitization
- Secure authentication flows

## 📈 Monitoring & Analytics

- Health check endpoints
- Azure Application Insights integration
- Performance monitoring
- Error tracking and logging

## 🛠️ Development Tools

- **VS Code Extensions**: Python, Azure, GitHub
- **Code Quality**: Black, Flake8, Pytest
- **Database**: Azure Data Studio
- **API Testing**: Postman or Thunder Client

## 📞 Support & Resources

### Paid Subscriptions Included
- ✅ **GitHub Developer Support**
- ✅ **ChatGPT Plus**
- ✅ **Azure Web App Services**
- ✅ **Stack.ai Integration**

### GitHub Policies
- Multiple laptop usage allowed with same account
- Private repositories included
- Unlimited collaborators on public repos

## 🚀 Getting Started Checklist

- [ ] Clone repository
- [ ] Set up Azure SQL Database
- [ ] Configure environment variables
- [ ] Run local development server
- [ ] Create GitHub repository
- [ ] Set up GitHub Actions secrets
- [ ] Deploy to Azure Web App Services
- [ ] Configure monitoring and alerts

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**Built with ❤️ using Azure Cloud Services and GitHub Actions**
