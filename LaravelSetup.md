
# Survey Management Project Setup (Backend)

## 1. Install XAMPP
- **Download XAMPP**: [XAMPP Official Site](https://www.apachefriends.org/index.html).
- **Start XAMPP**: Run Apache and MySQL via the XAMPP Control Panel.

## 2. Create Laravel Project in XAMPP
- **Navigate to `htdocs`**: Open the XAMPP folder `C:\xampp\htdocs`.
- **Create a Laravel Project**: Use Composer to create the project in `htdocs`:
  ```bash
  composer create-project --prefer-dist laravel/laravel survey_master_backend
  ```
- **Navigate to Project Folder**:
  ```bash
  cd survey_master_backend
  ```

## 3. Configure Database in Laravel (SQLite)

### 3.1 Create SQLite Database File
- Go to the `database/` folder of your Laravel project.
- Create a new SQLite database file:
  ```bash
  touch database/database.sqlite
  ```

### 3.2 Update `.env` File
- Edit the `.env` file to configure the SQLite database:
  ```env
  DB_CONNECTION=sqlite
  DB_DATABASE=/path_to_your_project/database/database.sqlite
  ```

### 3.3 Update `config/database.php`
- Ensure the `sqlite` connection is correctly set in `config/database.php`:
  ```php
  'sqlite' => [
      'driver' => 'sqlite',
      'database' => env('DB_DATABASE', database_path('database.sqlite')),
      'prefix' => '',
  ],
  ```

## 4. Run Laravel Migrations
- **Run Migrations**: To create tables in the SQLite database, run:
  ```bash
  php artisan migrate
  ```

## 5. Verify the Database
- Use **Laravel Tinker** to verify the database:
  ```bash
  php artisan tinker
  DB::connection('sqlite')->select('SELECT * FROM migrations');
  ```

Alternatively, use an **SQLite browser** (e.g., [DB Browser for SQLite](https://sqlitebrowser.org/)) to inspect the `database.sqlite` file.

---

## Conclusion:
- **XAMPP** provides a local development environment with Apache and MySQL (used later for production).
- **Laravel** is set up to use **SQLite** for local development.
- You’ve successfully configured the database, run migrations, and verified the setup.
