# Bakery Production Management System

A comprehensive web-based production management system designed specifically for bakery operations. This system streamlines production planning, recipe management, equipment tracking, order processing, and batch monitoring to help bakery managers efficiently manage their daily operations.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [System Requirements](#system-requirements)
- [Installation](#installation)
- [Database Setup](#database-setup)
- [Configuration](#configuration)
- [User Roles](#user-roles)
- [Project Structure](#project-structure)
- [Key Modules](#key-modules)
- [Usage Guide](#usage-guide)
- [API Endpoints](#api-endpoints)
- [Dependencies](#dependencies)
- [Security Features](#security-features)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

The Bakery Production Management System is a PHP-based web application that provides a complete solution for managing bakery production workflows. It enables administrators, supervisors, and bakers to collaborate effectively in scheduling production batches, managing recipes, tracking equipment usage, monitoring order fulfillment, and generating production reports.

### Key Benefits

- **Centralized Production Management**: Schedule and track all production batches from a single dashboard
- **Recipe Management**: Store and manage detailed recipes with ingredients, equipment requirements, and baking instructions
- **Equipment Tracking**: Monitor equipment availability and usage across different production batches
- **Order Processing**: Manage customer orders and link them to production schedules
- **Real-time Monitoring**: Track production status, quality tests, and batch completion
- **Role-based Access**: Different access levels for administrators, supervisors, and bakers

## ✨ Features

### 1. Production Management
- Schedule production batches with start and end dates
- Assign staff members to production batches
- Track production status (Ordered, In Progress, Finished)
- Monitor batch duration and completion
- Quality testing and comments for each batch
- Production timetable view

### 2. Recipe Management
- Create and manage recipes for different product types (Cake, Muffin, Croissant, Bread, Pizza, Pasta)
- Define ingredients with quantities and units
- Specify required equipment for each recipe
- Store detailed baking steps and instructions
- Link recipes to product categories

### 3. Equipment Management
- Categorize equipment into:
  - **Machines & Utility** (Mixers, Ovens, Refrigerators, etc.)
  - **Tools** (Rolling pins, Cutters, Knives, etc.)
  - **Bakeware** (Pans, Trays, Molds, etc.)
- Track equipment availability (used/not used)
- View equipment details including brand and model information
- Assign equipment to recipes

### 4. Order Management
- Create and manage customer orders
- Link orders to production schedules
- Track order status (Ordered, In Progress, Finished)
- View order history and reports

### 5. User Management
- Three user roles with different access levels:
  - **Administrator**: Full system access
  - **Supervisor/Researcher**: Production and recipe management
  - **Baker/Respondent**: Batch tracking and production reports
- User registration and authentication
- Password reset functionality

### 6. Batch Tracking
- Real-time batch status monitoring
- View assigned batches for bakers
- Track production progress
- Quality test recording

### 7. Reporting
- Production reports and logs
- Order history
- Equipment usage statistics
- User activity tracking

### 8. Survey System (Legacy Feature)
- Create and manage surveys
- Question management with multiple types (radio, checkbox, text field)
- Response collection and analysis

### 9. Contact & Messaging
- Contact form for customer inquiries
- Internal messaging system
- Email notifications (via PHPMailer)

## 🛠 Technology Stack

### Backend
- **PHP 8.0+** - Server-side scripting
- **MySQL/MariaDB** - Database management
- **PDO** - Database abstraction layer

### Frontend
- **HTML5/CSS3** - Markup and styling
- **Bootstrap 4** - Responsive UI framework
- **AdminLTE 3** - Admin dashboard template
- **jQuery** - JavaScript library
- **DataTables** - Advanced table features
- **Select2** - Enhanced select dropdowns
- **SweetAlert2** - Beautiful alert dialogs
- **Toastr** - Notification library
- **Font Awesome** - Icon library

### Third-party Libraries
- **PHPMailer 6.7+** - Email functionality

## 💻 System Requirements

### Server Requirements
- **Web Server**: Apache 2.4+ or Nginx
- **PHP**: Version 8.0 or higher
- **Database**: MySQL 5.7+ or MariaDB 10.4+
- **PHP Extensions**:
  - PDO
  - PDO_MySQL
  - mbstring
  - openssl (for email functionality)

### Client Requirements
- Modern web browser (Chrome, Firefox, Safari, Edge)
- JavaScript enabled
- Internet connection (for CDN resources)

## 📦 Installation

### Step 1: Clone or Download the Project

```bash
# If using Git
git clone <repository-url>
cd survey

# Or download and extract the ZIP file to your web server directory
```

### Step 2: Place Files in Web Server Directory

For XAMPP (Windows):
```
C:\xampp\htdocs\survey\
```

For WAMP (Windows):
```
C:\wamp64\www\survey\
```

For LAMP (Linux):
```
/var/www/html/survey/
```

### Step 3: Install Dependencies

Navigate to the project directory and install Composer dependencies:

```bash
composer install
```

This will install PHPMailer and other required packages.

### Step 4: Database Setup

1. Open phpMyAdmin or your MySQL client
2. Create a new database named `survey_db`
3. Import the SQL file:
   ```sql
   -- Import database/survey_db.sql
   ```

Or via command line:
```bash
mysql -u root -p survey_db < database/survey_db.sql
```

### Step 5: Configure Database Connection

Edit `includes/dbconnection.php`:

```php
define('DB_HOST', 'localhost');
define('DB_USER', 'root');        // Your MySQL username
define('DB_PASS', '');            // Your MySQL password
define('DB_NAME', 'survey_db');   // Database name
```

## 🗄 Database Setup

The system uses the following main database tables:

### Core Tables
- `users` - User accounts and authentication
- `staff_information` - Staff member details
- `typeproduct` - Product categories
- `receipe` - Recipe information
- `ing_list` - Recipe ingredients
- `equipment_list` - Equipment categories
- `equipment_details` - Equipment specifications
- `recipe_equipment` - Recipe-equipment relationships
- `categories` - Production batches
- `order_customer` - Customer orders
- `contact` - Contact form submissions

### Survey Tables (Legacy)
- `survey_set` - Survey definitions
- `questions` - Survey questions
- `answers` - Survey responses

## ⚙️ Configuration

### Database Configuration
Update database credentials in `includes/dbconnection.php`:

```php
define('DB_HOST', 'localhost');
define('DB_USER', 'your_username');
define('DB_PASS', 'your_password');
define('DB_NAME', 'survey_db');
```

### Email Configuration (Optional)
If you want to use email features, configure PHPMailer settings in relevant files (e.g., `forgot-password.php`, `contact.php`).

### Session Configuration
The system uses PHP sessions. Ensure sessions are properly configured in `php.ini`.

## 👥 User Roles

### 1. Administrator (Type 1)
**Default Credentials:**
- Email: `admin@admin.com`
- Password: `admin` (MD5 hashed)

**Permissions:**
- Full system access
- User management (create, edit, delete users)
- Production management
- Recipe management
- Equipment management
- Order management
- Survey management
- System settings
- View all statistics and reports

### 2. Supervisor/Researcher (Type 2)
**Permissions:**
- Production scheduling and management
- Recipe creation and editing
- Equipment viewing
- Order message management
- Production reports
- Batch status updates
- Quality test recording

### 3. Baker/Respondent (Type 3)
**Permissions:**
- View assigned production batches
- Batch tracking
- Update batch status
- View production reports
- Limited access to system features

## 📁 Project Structure

```
survey/
├── assets/                 # Static assets
│   ├── dist/              # Compiled CSS/JS
│   │   ├── css/
│   │   ├── js/
│   │   └── img/
│   └── plugins/           # Third-party plugins
├── css/                   # Custom stylesheets
├── database/              # Database files
│   └── survey_db.sql     # Database schema
├── images/                # Image assets
├── includes/              # Core includes
│   ├── dbconnection.php  # Database connection (PDO)
│   ├── header.php        # Header template
│   └── footer.php        # Footer template
├── vendor/                # Composer dependencies
│   └── phpmailer/        # PHPMailer library
├── about.php             # About page
├── admin_class.php       # Admin operations class
├── ajax.php              # AJAX handlers
├── apply_equipment.php   # Equipment application
├── batch_tracking.php   # Batch tracking page
├── check_schedule.php    # Schedule validation
├── contact.php           # Contact form
├── db_connect.php        # Database connection (MySQLi)
├── edit_order.php        # Edit order form
├── edit_production.php   # Edit production form
├── edit_recipe.php       # Edit recipe form
├── edit_template.php     # Edit template form
├── edit_user.php         # Edit user form
├── fetch_equipment.php   # Equipment data fetcher
├── fetch_ingredients.php # Ingredients data fetcher
├── footer.php            # Footer component
├── forgot-password.php   # Password reset
├── get_recipes.php       # Recipe data API
├── header.php            # Header component
├── home.php              # Dashboard/home page
├── homepage.php          # Public homepage
├── index.php             # Main application entry
├── login.php             # Login page
├── manage_question.php   # Question management
├── manage_recipe.php     # Recipe management
├── manage_user.php       # User management
├── new_message.php       # New message form
├── new_product.php      # New product form
├── new_recipe.php        # New recipe form
├── order_log.php         # Order history
├── order_message.php     # Order messages
├── present_timetable.php # Production timetable
├── process_finished.php  # Production completion handler
├── production.php        # Production management
├── registration.php      # User registration
├── reset_password.php    # Password reset handler
├── schedule_production.php # Production scheduling
├── sidebar.php           # Sidebar navigation
├── topbar.php            # Top navigation bar
├── view_details.php      # View details modal
├── view_equipment.php    # Equipment viewer
├── view_production.php   # Production viewer
├── view_recipe.php       # Recipe viewer
├── composer.json         # Composer dependencies
└── composer.lock         # Composer lock file
```

## 🔑 Key Modules

### Production Management Module
**Files**: `production.php`, `schedule_production.php`, `edit_production.php`, `process_finished.php`

**Features**:
- Create production schedules
- Assign staff to batches
- Track production status
- Record quality tests
- View production timetable

### Recipe Management Module
**Files**: `manage_recipe.php`, `new_recipe.php`, `edit_recipe.php`, `view_recipe.php`

**Features**:
- Create and edit recipes
- Manage ingredients with quantities
- Assign equipment to recipes
- Store baking instructions
- Link recipes to products

### Equipment Management Module
**Files**: `view_equipment.php`, `apply_equipment.php`, `fetch_equipment.php`

**Features**:
- View equipment inventory
- Track equipment usage
- Categorize equipment
- Monitor availability

### Order Management Module
**Files**: `order_message.php`, `order_log.php`, `edit_order.php`

**Features**:
- Create customer orders
- Link orders to production
- Track order status
- View order history

### User Management Module
**Files**: `manage_user.php`, `edit_user.php`, `registration.php`

**Features**:
- Create user accounts
- Assign roles
- Update user information
- Link users to staff records

## 📖 Usage Guide

### For Administrators

1. **Login**: Access the system using admin credentials
2. **Dashboard**: View system statistics and quick access to modules
3. **User Management**: Create accounts for supervisors and bakers
4. **Product Management**: Add new product types (Cake, Bread, etc.)
5. **Recipe Management**: Create recipes with ingredients and equipment
6. **Production Scheduling**: Schedule production batches
7. **Monitoring**: Track all production activities

### For Supervisors

1. **Login**: Use supervisor credentials
2. **Order Management**: View and process customer orders
3. **Production Scheduling**: Create production schedules
4. **Recipe Management**: Create and edit recipes
5. **Quality Control**: Record quality tests and comments
6. **Reports**: Generate production reports

### For Bakers

1. **Login**: Use baker credentials
2. **Batch Tracking**: View assigned production batches
3. **Status Updates**: Update batch completion status
4. **Reports**: View production reports

### Creating a Production Schedule

1. Navigate to **Production** → **Schedule Production**
2. Select an **Order ID** from pending orders
3. Choose a **Product Type** and **Recipe**
4. Enter **Quantity** of products
5. Select **Staff ID** (Person in Charge)
6. Set **Start Date** and **End Date**
7. Enter **Duration** in hours
8. Click **Save** to create the schedule

### Creating a Recipe

1. Navigate to **Recipe Management** → **Add New Recipe**
2. Enter **Recipe Name**
3. Select **Product Type**
4. Add **Ingredients** with quantities and units
5. Select **Required Equipment**
6. Enter **Baking Steps**
7. Save the recipe

## 🔌 API Endpoints

The system uses AJAX for dynamic operations. Key endpoints:

- `ajax.php` - Main AJAX handler for various operations
- `get_recipes.php` - Fetch recipes based on product type
- `fetch_equipment.php` - Fetch equipment data
- `fetch_ingredients.php` - Fetch ingredient data

## 📦 Dependencies

### PHP Dependencies (via Composer)
```json
{
    "require": {
        "phpmailer/phpmailer": "^6.7"
    }
}
```

### Frontend Dependencies (via CDN)
- Bootstrap 4
- jQuery
- DataTables
- Select2
- SweetAlert2
- Toastr
- Font Awesome
- AdminLTE 3

## 🔒 Security Features

- **Password Hashing**: Uses MD5 (legacy) and bcrypt for password storage
- **Session Management**: PHP sessions for user authentication
- **SQL Injection Prevention**: Uses prepared statements (PDO)
- **Input Validation**: Server-side validation for user inputs
- **Role-based Access Control**: Different access levels for different user types
- **XSS Protection**: HTML escaping in output (htmlspecialchars)

### Security Recommendations

⚠️ **Important**: The system currently uses MD5 for some password hashing. It's recommended to:
1. Migrate to bcrypt or Argon2 for all passwords
2. Implement CSRF protection
3. Add rate limiting for login attempts
4. Use HTTPS in production
5. Regularly update dependencies

## 🐛 Troubleshooting

### Common Issues

**1. Database Connection Error**
- Check database credentials in `includes/dbconnection.php`
- Ensure MySQL service is running
- Verify database `survey_db` exists

**2. Session Issues**
- Check PHP session configuration
- Ensure `session_start()` is called before output
- Verify session directory permissions

**3. Composer Dependencies Not Loading**
- Run `composer install` in project root
- Check `vendor/autoload.php` exists

**4. CSS/JS Not Loading**
- Check file paths in `header.php` and `footer.php`
- Verify `assets/` directory exists
- Check web server document root configuration

**5. Permission Denied Errors**
- Ensure web server has read permissions
- Check file ownership
- Verify PHP can write to session directory

### Debug Mode

To enable error reporting for debugging, add to the top of PHP files:

```php
error_reporting(E_ALL);
ini_set('display_errors', 1);
```

**Remember to disable this in production!**

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Code Style Guidelines
- Follow PSR-12 coding standards
- Use meaningful variable and function names
- Add comments for complex logic
- Keep functions focused and small

## 📝 License

This project is proprietary software. All rights reserved.

## 📞 Support

For support and inquiries:
- Check the documentation
- Review the database schema
- Examine the code comments
- Contact the development team

## 🎯 Future Enhancements

Potential improvements for future versions:
- [ ] Mobile app integration
- [ ] Real-time notifications
- [ ] Advanced analytics and reporting
- [ ] Inventory management system
- [ ] Barcode scanning for equipment
- [ ] Automated production scheduling
- [ ] Integration with POS systems
- [ ] Multi-language support
- [ ] API documentation
- [ ] Unit testing suite

## 📊 System Statistics

The system tracks:
- Total production batches
- Active users (by role)
- Recipe count
- Equipment inventory
- Order statistics
- Survey responses (if used)

---

**Version**: 1.0  
**Last Updated**: January 2025  
**Maintained By**: Development Team

---

*For detailed technical documentation, please refer to the inline code comments and database schema.*
#   B a k e r y - P r o d u c t i o n - M a n a g e m e n t - S y s t e m  
 