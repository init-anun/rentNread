# RentNRead - Book Renting Platform

RentNRead is a Django-based web application designed to facilitate book renting, categorization, search, and user reviews. It provides a complete experience from user profiles and Google authentication to checking out a dynamic renting cart.

---

## 🚀 Key Features

### 1. User Authentication & Profiles
- **Custom Authorization**: Dedicated sign-up, sign-in, and sign-out pages with standard password verification.
- **Google OAuth Integration**: Built-in social login capability using the `django-allauth` library.
- **Password Recovery**: Complete password reset workflow using email notifications (SMTP integration).
- **User Profiles**: Automatic profile generation (`Profile` model) on user creation using Django signals.

### 2. Catalog & Discovery
- **Genre & Categories Filter**: Books can be organized into categories (e.g., "Top Rated", "Nepali", etc.).
- **Smart Book Showcase**: Clean grid displays including dynamic star ratings and covers.
- **Title Search**: Rapid search filter on titles to locate books quickly.
- **Detailed Book View**: Displays the book description, rating, user reviews, and recommendations for related books.

### 3. Ratings & Reviews
- **Feedback Loop**: Registered users can submit text reviews and choose a rating between 0 and 5 stars.
- **Dynamic Star Calculation**: Computes the average rating of each book and dynamically renders star icons in templates.

### 4. Shopping Cart & Checkout Flow
- **AJAX Cart Operations**: Users can add or remove books from their cart asynchronously.
- **Shipping Details**: Form for collecting shipping info (state, city, address, phone number) on checkout.
- **Cart Calculations**: Calculates the number of items and the total price automatically.

---

## 🛠️ Tech Stack

- **Backend**: Django 4.0.5 (Python)
- **Frontend**: HTML5, Vanilla CSS, JavaScript (Fetch API for dynamic interactions)
- **Database**: PostgreSQL (configured via environment variables)
- **Environment Management**: `python-decouple` for `.env` integration
- **Social Auth**: `django-allauth`

---

## ⚙️ Setup & Installation

To run the project locally, follow these steps:

### 1. Clone the Repository
```bash
git clone <repository-url>
cd rentNread
```

### 2. Configure a Virtual Environment
Create and activate a Python virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies
Install the required packages. A typical environment includes:
- `django`
- `python-decouple`
- `django-allauth`
- `psycopg2-binary` (or `psycopg2` for PostgreSQL connection)

### 4. Set Up Environment Variables
Create a `.env` file in the root directory (next to `manage.py`):
```ini
# Django Security
SECRET_KEY=your_django_secret_key

# PostgreSQL Connection Details
DATABASE_NAME=your_database_name
DATABASE_USER=your_database_user
DATABASE_PASS=your_database_password

# Email (SMTP) for password recovery
EMAIL_ADDRESS=your_email@gmail.com
EMAIL_PASSWORD=your_email_app_password

# Google OAuth Credentials
CLIENT_ID=your_google_client_id.apps.googleusercontent.com
SECRET=your_google_client_secret
```

### 5. Run Migrations
Apply database migrations to configure the database schema:
```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Create an Admin Account
To access the Django admin portal (`/admin`):
```bash
python manage.py createsuperuser
```

### 7. Launch Development Server
```bash
python manage.py runserver
```
Navigate to `http://127.0.0.1:8000/` in your browser.

---

## 📁 Directory Structure

- **[Rent](./Rent)**: Manages book catalog, categories, reviews, FAQs, cart management, and checkout.
  - `models.py`: Defines core data schemas (`Books`, `Category`, `BookReview`, `FAQ`, `Order`, `OrderItem`, and `ShippingDetails`).
  - `views.py`: Application views handling book displays, detail pages, category filters, and checkout.
- **[users](./users)**: Handles registration, login, and user profile profiles.
  - `models.py`: Extends `User` model with `Profile`.
  - `signals.py`: Automated receiver to construct `Profile` rows.
- **[RentNRead](./RentNRead)**: Settings, configurations, global urls, and wsgi/asgi setup.
- **[templates](./templates)**: Base structures and components.
