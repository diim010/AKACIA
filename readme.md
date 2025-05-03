            # Unit testsakaCIA Laravel + Filament Setup Documentation
1. System Requirements

    OS: Windows 10/11 (64-bit recommended)

    Web Server: XAMPP (Apache, MySQL)

    PHP: 8.1 or higher

    Composer: Latest version

    Database: MySQL (via XAMPP)

    Extensions:

        OpenSSL

        PDO MySQL

        Mbstring

        GD

        XML

        Ctype

        JSON

        Tokenizer

2. Installation Steps
2.1. Install XAMPP

    Download XAMPP (PHP 8.1+)

    Run installer and select:

        Apache

        MySQL

        PHP 8.1+

    Complete installation and launch XAMPP Control Panel.

2.2. Enable Required PHP Extensions

    Open C:\xampp\php\php.ini

    Uncomment (remove ;) these lines:
    ini

    extension=openssl
    extension=mbstring
    extension=pdo_mysql
    extension=gd
    extension=fileinfo

    Save and restart Apache in XAMPP.

2.3. Install Composer

    Download Composer for Windows

    Run the installer and ensure:

        "Add to PATH" is checked.

        "Use PHP from XAMPP" is selected.

2.4. Create Laravel Project

    Open Command Prompt (cmd) as Administrator.

    Navigate to htdocs:
    sh

cd C:\xampp\htdocs

Create Laravel project:
sh

    composer create-project laravel/laravel akaCIA
    cd akaCIA

2.5. Configure Database

    Open phpMyAdmin (http://localhost/phpmyadmin)

    Create a new database: akaCIA

    Update .env file:
    ini

    DB_DATABASE=akaCIA
    DB_USERNAME=root
    DB_PASSWORD=

2.6. Install Filament Admin Panel

    Install Filament:
    sh

composer require filament/filament:"^3.0" -W

Set up Filament:
sh

php artisan filament:install --panels

Create an admin user:
sh

    php artisan make:filament-user

2.7. Run Migrations
sh

php artisan migrate

2.8. Start Development Server
sh

php artisan serve

    Frontend: http://localhost:8000

    Admin Panel: http://localhost:8000/admin

3. Troubleshooting Common Issues
3.1. PHP Version Too Low

    Error: filament/filament requires PHP ^8.1

    Solution:

        Upgrade XAMPP to PHP 8.1+

        Or use Laragon (easier PHP version switching)

3.2. OpenSSL Missing

    Error: The openssl extension is required for SSL/TLS

    Solution:

        Uncomment extension=openssl in php.ini

        Restart Apache

3.3. Composer Memory Limit

    Error: Allowed memory size exhausted

    Solution:
    sh

    php -d memory_limit=-1 composer install

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

3.4. File Permissions (Windows)

    Error: storage/logs not writable

    Solution:

        Right-click akaCIA/storage → Properties → Security → Edit → Add "Everyone" with Full Control

4. Next Steps

    Create Resources:
    sh

php artisan make:filament-resource Post

Customize Admin Panel:
Edit config/filament.php

Add Authentication:
sh

    composer require laravel/breeze --dev
    php artisan breeze:install

5. Conclusion

Your Laravel + Filament admin panel (akaCIA) is now ready!
For production, consider:

    Using Laravel Forge or Laravel Sail

    Setting up proper user roles & permissions

    Configuring email services

Need further help?
Check the Filament Docs or Laravel Documentation.
📌 Notes

    Always backup your database before migrations.

    Use git for version control.

    For better performance, consider OPcache in php.ini.

🚀 Happy Coding! 🚀




### Srructure
akaCIA/
├── app/
│   ├── Actions/             # Single purpose classes for business logic
│   ├── Console/             # Console commands
│   ├── Exceptions/          # Exception handlers
│   ├── Filament/            # Filament admin panel resources
│   │   ├── Resources/       # Admin panel resources (CRUD)
│   │   ├── Widgets/         # Admin panel widgets
│   │   └── Pages/           # Admin panel custom pages
│   ├── Http/
│   │   ├── Controllers/     # API and web controllers
│   │   │   ├── Api/         # API controllers (versioned)
│   │   │   └── Web/         # Web controllers
│   │   ├── Middleware/      # Application middleware
│   │   └── Requests/        # Form requests for validation
│   ├── Jobs/                # Queue jobs
│   ├── Listeners/           # Event listeners
│   ├── Models/              # Eloquent models
│   ├── Notifications/       # Notification classes
│   ├── Policies/            # Model policies for authorization
│   ├── Providers/           # Service providers
│   ├── Repositories/        # Data access layer
│   ├── Services/            # Business logic services
│   └── Support/             # Helper classes and utilities
├── bootstrap/               # Framework bootstrap files
├── config/                  # Configuration files
├── database/
│   ├── factories/           # Model factories
│   ├── migrations/          # Database migrations
│   └── seeders/             # Database seeders
├── public/                  # Publicly accessible files
├── resources/
│   ├── css/                 # CSS and SCSS files
│   ├── js/                  # JavaScript files
│   └── views/               # Blade templates
├── routes/
│   ├── api.php              # API routes
│   ├── channels.php         # Broadcast channels
│   ├── console.php          # Console routes
│   └── web.php              # Web routes
├── storage/                 # Storage for logs, cache, uploads, etc.
└── tests/                   # Tests
    ├── Feature/             # Feature tests
    └── Unit/    