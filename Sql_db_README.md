# Azure SQL Mini Project

A comprehensive mini project demonstrating full-stack integration of Azure SQL Server, GitHub, GitHub Actions, and Azure Web App Services with proper branch management and automated CI/CD deployment.

## 🏗️ Project Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   GitHub Repo   │────│  GitHub Actions  │────│  Azure Web App  │
│                 │    │     CI/CD        │    │                 │
│  ┌─────────────┐│    │                  │    │  ┌─────────────┐│
│  │dev-database ││────│  Development     │────│  │   Dev Env   ││
│  └─────────────┘│    │  Pipeline        │    │  └─────────────┘│
│  ┌─────────────┐│    │                  │    │  ┌─────────────┐│
│  │    main     ││────│  Staging         │────│  │ Staging Env ││
│  └─────────────┘│    │  Pipeline        │    │  └─────────────┘│
│  ┌─────────────┐│    │                  │    │  ┌─────────────┐│
│  │prod-database││────│  Production      │────│  │  Prod Env   ││
│  └─────────────┘│    │  Pipeline        │    │  └─────────────┘│
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                                         │
                                                         ▼
                                               ┌─────────────────┐
                                               │ Azure SQL       │
                                               │ Server          │
                                               │ ┌─────────────┐ │
                                               │ │   Dev DB    │ │
                                               │ └─────────────┘ │
                                               │ ┌─────────────┐ │
                                               │ │   Prod DB   │ │
                                               │ └─────────────┘ │
                                               └─────────────────┘
```

## 🌿 Branch Strategy & Deployment Flow

### Branch Structure
- **`dev-database`**: Development branch for active development
- **`main`**: Staging branch for testing and integration
- **`production-database`**: Production branch for live deployments

### Deployment Pipeline
1. **Development**: Push to `dev-database` → Auto-deploy to Development Environment
2. **Staging**: Merge `dev-database` to `main` → Auto-deploy to Staging Environment
3. **Production**: Merge `main` to `production-database` → Auto-deploy to Production Environment

## 💰 Cost Structure & Support Plans

### Azure Resources (Monthly Estimates)
| Environment | SQL Database | Web App | App Insights | Total |
|-------------|--------------|---------|--------------|-------|
| **Development** | Basic ($4.99) | B1 ($13.14) | Pay-as-go ($0-2) | **$18-20** |
| **Staging** | Basic ($4.99) | B1 ($13.14) | Pay-as-go ($0-2) | **$18-20** |
| **Production** | S0 ($15.00) | B2 ($26.28) | Pay-as-go ($0-5) | **$41-46** |
| **Total Monthly** | | | | **$77-86** |

### Support Plans
| Service | Plan | Monthly Cost | Benefits |
|---------|------|--------------|----------|
| **GitHub** | Team | $4/user | Private repos, advanced collaboration |
| **Azure** | Developer | $29 | Technical support, architectural guidance |
| **Total Support** | | **$33** | Professional development support |

**Grand Total: $110-119/month** (All environments + support)

## 🚀 Features

- ✅ RESTful API with Express.js
- ✅ Azure SQL Database integration
- ✅ Cost tracking and monitoring
- ✅ GitHub Actions CI/CD pipeline
- ✅ Security best practices
- ✅ Environment management (dev/staging/prod)
- ✅ Automated testing
- ✅ Error handling and logging
- ✅ Rate limiting
- ✅ Health checks

## 📋 Prerequisites

### Local Development
- Node.js 18+ ([Download here](https://nodejs.org/))
- Git ([Download here](https://git-scm.com/))
- Azure CLI ([Install guide](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli))

### Azure Resources Required
- Azure Subscription
- Azure SQL Database
- Azure Web App Service
- Application Insights (optional but recommended)

## 🛠️ Setup Instructions

### 1. Clone and Install Dependencies

```bash
# Clone the repository
git clone <your-repo-url>
cd sql_db

# Install Node.js dependencies
npm install
```

### 2. Environment Configuration

```bash
# Copy environment template
copy .env.example .env

# Edit .env with your Azure SQL Database credentials
# DB_SERVER=your-server.database.windows.net
# DB_NAME=your-database-name
# DB_USER=your-username
# DB_PASSWORD=your-password
```

### 3. Azure SQL Database Setup

#### Create Azure SQL Database
```bash
# Login to Azure
az login

# Create resource group
az group create --name rg-webapp-dev --location "East US"

# Create SQL Server
az sql server create \
  --name your-sql-server \
  --resource-group rg-webapp-dev \
  --location "East US" \
  --admin-user your-admin \
  --admin-password "YourPassword123!"

# Create SQL Database
az sql db create \
  --resource-group rg-webapp-dev \
  --server your-sql-server \
  --name your-database \
  --service-objective Basic
```

#### Configure Firewall
```bash
# Allow Azure services
az sql server firewall-rule create \
  --resource-group rg-webapp-dev \
  --server your-sql-server \
  --name AllowAzureServices \
  --start-ip-address 0.0.0.0 \
  --end-ip-address 0.0.0.0

# Allow your IP (replace with your actual IP)
az sql server firewall-rule create \
  --resource-group rg-webapp-dev \
  --server your-sql-server \
  --name AllowMyIP \
  --start-ip-address YOUR.IP.ADDRESS \
  --end-ip-address YOUR.IP.ADDRESS
```

### 4. Azure Web App Setup

```bash
# Create App Service Plan
az appservice plan create \
  --name plan-webapp-dev \
  --resource-group rg-webapp-dev \
  --sku B1 \
  --is-linux

# Create Web App
az webapp create \
  --resource-group rg-webapp-dev \
  --plan plan-webapp-dev \
  --name your-unique-webapp-name \
  --runtime "NODE|18-lts"

# Configure environment variables
az webapp config appsettings set \
  --resource-group rg-webapp-dev \
  --name your-unique-webapp-name \
  --settings \
    NODE_ENV=production \
    DB_SERVER=your-server.database.windows.net \
    DB_NAME=your-database \
    DB_USER=your-admin \
    DB_PASSWORD="YourPassword123!"
```

## 🏃‍♂️ Running the Application

### Local Development
```bash
# Start development server
npm run dev

# The app will be available at http://localhost:3000
```

### Production Build
```bash
# Install production dependencies only
npm ci --only=production

# Start production server
npm start
```

## 🧪 Testing

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run linting
npm run lint

# Fix linting issues
npm run lint:fix
```

## 📊 API Endpoints

### Health Check
```
GET /health
```

### Users Management
```
GET /api/users          # Get all users
POST /api/users         # Create new user
Body: { "username": "string", "email": "string" }
```

### Cost Tracking
```
GET /api/costs          # Get cost summary
POST /api/costs         # Record new cost
Body: {
  "service_name": "string",
  "cost_amount": number,
  "currency": "string",
  "billing_period": "YYYY-MM",
  "notes": "string"
}
```

## 🔄 DevOps Workflow

### Branching Strategy
```
main (production)
├── develop (staging)
    ├── feature/user-auth
    ├── feature/cost-alerts
    └── hotfix/security-patch
```

### CI/CD Pipeline
1. **Pull Request** → Runs tests, linting, security scans
2. **Merge to develop** → Deploys to staging environment
3. **Merge to main** → Deploys to production environment

### GitHub Secrets Required
```
AZURE_WEBAPP_PUBLISH_PROFILE          # Production deployment profile
AZURE_WEBAPP_PUBLISH_PROFILE_STAGING  # Staging deployment profile
SNYK_TOKEN                            # Security scanning token
```

## 📈 Monitoring and Cost Management

### Cost Tracking Features
- Automated cost recording for Azure services
- Monthly budget alerts
- Cost breakdown by service
- Historical cost analysis

### Monitoring Setup
```bash
# Create Application Insights
az monitor app-insights component create \
  --app your-app-insights \
  --location "East US" \
  --resource-group rg-webapp-dev \
  --application-type web
```

## 🛡️ Security Best Practices

- ✅ Environment variables for sensitive data
- ✅ SQL injection prevention with parameterized queries
- ✅ Rate limiting to prevent abuse
- ✅ Helmet.js for security headers
- ✅ CORS configuration
- ✅ Input validation
- ✅ Error handling without information leakage

## 🔧 Troubleshooting

### Common Issues

#### Database Connection Fails
```bash
# Check firewall rules
az sql server firewall-rule list \
  --resource-group rg-webapp-dev \
  --server your-sql-server

# Test connection
npm run test:db-connection
```

#### Application Won't Start
```bash
# Check logs
az webapp log tail \
  --resource-group rg-webapp-dev \
  --name your-webapp-name
```

### Environment-Specific Issues

#### Development
- Ensure Node.js 18+ is installed
- Check `.env` file configuration
- Verify database connectivity

#### Production
- Check Azure Web App configuration
- Verify environment variables in Azure Portal
- Review Application Insights logs

## 📚 Additional Resources

- [Azure SQL Database Documentation](https://docs.microsoft.com/en-us/azure/azure-sql/)
- [Azure App Service Documentation](https://docs.microsoft.com/en-us/azure/app-service/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

For support and questions:
- Create an issue in this repository
- Review the troubleshooting section
- Check Azure documentation for service-specific issues

---

**Estimated Setup Time:** 30-45 minutes  
**Monthly Cost:** $18-20 USD  
**Skill Level:** Intermediate
