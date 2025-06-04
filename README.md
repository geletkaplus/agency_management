# Agency Management System

A comprehensive Django application for managing digital agency operations including revenue tracking, project allocation, capacity planning, and profitability analysis.

## 🚀 Features

### Core Functionality
- **Multi-Company Support**: Manage multiple agencies/companies within one system
- **Revenue Management**: Track both booked and forecast revenue
- **Project Management**: Comprehensive project tracking with team allocations
- **Capacity Planning**: Monitor team utilization and capacity
- **Cost Tracking**: Track payroll, contractor, and operating expenses
- **Profitability Analysis**: Real-time profit margins and financial metrics

### Dashboards
- **Admin Dashboard**: Complete overview with revenue charts and metrics
- **Project Manager Dashboard**: PM-specific view of managed projects
- **Employee Dashboard**: Individual contributor view with personal allocations
- **User View Switching**: Admins can view the system as any user

### Key Features
- Monthly hour allocation grid for projects
- Revenue visualization with Chart.js
- Excel import functionality for bulk data
- Role-based access control
- Responsive design with Tailwind CSS

## 📋 Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- Git

## 🛠️ Local Development Setup

### 1. Clone the Repository
```bash
git clone <repository-url>
cd agency_management
```

### 2. Create Virtual Environment
```bash
python3 -m venv venv
```

### 3. Activate Virtual Environment
**macOS/Linux:**
```bash
source venv/bin/activate
```

**Windows:**
```bash
venv\Scripts\activate
```

### 4. Install Dependencies
```bash
pip install -r requirements.txt
```

### 5. Run Database Migrations
```bash
python manage.py migrate
```

### 6. Create Superuser
```bash
python manage.py createsuperuser
```
Follow the prompts to create your admin account.

### 7. (Optional) Load Sample Data
```bash
# Generate test revenue data
python manage.py generate_test_revenue

# Or import from spreadsheet
python manage.py import_spreadsheet path/to/excel/file.xlsx COMPANY_CODE
```

### 8. Run Development Server
```bash
python manage.py runserver
```

Visit http://localhost:8000 to access the application.

## 🗄️ Database Structure

### Key Models
- **Company**: Multi-company support
- **UserProfile**: Extended user model with roles and capacity
- **Client**: Client organizations
- **Project**: Projects with revenue tracking
- **ProjectAllocation**: Monthly hour allocations per team member
- **MonthlyRevenue**: Revenue tracking by month
- **Cost**: Unified cost tracking model

### User Roles
- Leadership
- Account Management
- Creative
- Technology
- Media
- Operations

## 🔑 Key URLs

- `/` - Dashboard (redirects based on user role)
- `/admin/` - Django Admin Interface
- `/agency/projects/` - Projects list
- `/agency/clients/` - Clients list
- `/agency/team/` - Team members
- `/agency/capacity/` - Capacity planning

## 💻 Common Development Tasks

### Reset Database
```bash
rm db.sqlite3
python manage.py migrate
python manage.py createsuperuser
```

### Import Data from Excel
```bash
python manage.py import_spreadsheet data.xlsx MAIN --dry-run  # Preview
python manage.py import_spreadsheet data.xlsx MAIN           # Import
```

### Make a User a Project Manager
```bash
python manage.py shell
>>> from agency.models import UserProfile
>>> profile = UserProfile.objects.get(user__username='username')
>>> profile.is_project_manager = True
>>> profile.save()
```

### Generate Test Data
```bash
python manage.py generate_test_revenue --years=2024,2025
```

## 🎨 Frontend Technologies

- **Tailwind CSS**: Utility-first CSS framework
- **Chart.js**: Revenue and metrics visualization
- **Vanilla JavaScript**: Dashboard interactivity

## 📊 Dashboard Features

### Admin Dashboard
- Monthly/Annual revenue overview
- Booked vs Forecast revenue breakdown
- Operating expense tracking
- Profit margins
- Team capacity utilization
- Interactive date range selection

### PM Dashboard
- Managed projects overview
- Team allocation status
- Project health indicators
- Revenue under management

### Employee Dashboard
- Personal hour allocations
- Utilization rate tracking
- Historical allocation trends
- Upcoming project assignments

## 🔧 Configuration

### Settings
- Development: `agency_management/settings.py`
- Production: `agency_management/settings_production.py`

### Environment Variables (Production)
```bash
SECRET_KEY=your-secret-key
DEBUG=False
ALLOWED_HOSTS=yourdomain.com,www.yourdomain.com
DB_NAME=agency_management
DB_USER=postgres
DB_PASSWORD=your-db-password
DB_HOST=localhost
DB_PORT=5432
```

## 🚦 Project Status Workflow
1. **Planning**: Initial project setup
2. **Active**: Ongoing work
3. **On Hold**: Temporarily paused
4. **Completed**: Finished projects
5. **Cancelled**: Terminated projects

## 🐛 Troubleshooting

### Common Issues

**Migration Errors**
```bash
python manage.py migrate --run-syncdb
```

**Static Files Not Loading**
```bash
python manage.py collectstatic
```

**User Profile Missing**
```bash
python manage.py shell
>>> from django.contrib.auth.models import User
>>> from agency.models import Company, UserProfile
>>> user = User.objects.get(username='admin')
>>> company = Company.objects.first()
>>> UserProfile.objects.create(user=user, company=company, role='leadership')
```

## 📝 Development Guidelines

1. **Always use virtual environment**
2. **Run migrations after model changes**
3. **Test user switching functionality as admin**
4. **Verify revenue calculations span project dates correctly**
5. **Check capacity calculations account for 4.33 weeks/month**

## 🔒 Security Considerations

- Admin users can view as other users (session-based)
- Payroll information restricted to superusers
- CSRF protection enabled
- SQL injection protection via Django ORM
- XSS protection via template escaping

## 📦 Deployment

For production deployment:
1. Set `DEBUG=False`
2. Configure proper `ALLOWED_HOSTS`
3. Use PostgreSQL instead of SQLite
4. Set up proper static file serving
5. Configure HTTPS
6. Set strong `SECRET_KEY`

## 🤝 Contributing

1. Create feature branch
2. Make changes
3. Test thoroughly
4. Submit pull request

## 📄 License

[Your License Here]

## 📞 Support

For questions or issues, contact [your-email@example.com]