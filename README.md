# 📚 Liane's Library System

A very basic personal library management app built with **Python**, **Streamlit**, and **MySQL**. It lets you track your book collection, manage friends who borrow books, and keep an overview of active loans — all through a clean web interface.

---

## Features
- **Inventory** — View all books and registered borrowers at a glance
- **Add Book** — Add new books (title + author) to your collection
- **Add Friend** — Register friends who can borrow books
- **Create Loan** — Lend a book to a friend, with automatic 14-day return deadline
- **Return Loan** — Mark a book as returned and close the loan

---

## Tech Stack
| Layer     | Technology                          |
|-----------|-------------------------------------|
| Frontend  | [Streamlit](https://streamlit.io)   |
| Backend   | Python 3, SQLAlchemy                |
| Database  | MySQL 8                             |
| Driver    | PyMySQL                             |

---

## Database Schema
Three tables connected by foreign keys:

```
books        (BookID, Title, Author, Isbn)
borrowers    (BorrowerID, FirstName, LastName, Email, PhoneNumber, MaxToBorrow)
loans        (LoanID, BookID → books, BorrowerID → borrowers, BorrowDate, ScheduledReturnDate, ReturnDate)
```

The SQL dump with sample data (German classics + test borrowers) is in `src/liane_library.sql`.

---

## Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/lianes-library.git
cd lianes-library
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Set up the database
Make sure MySQL is running locally, then import the schema and sample data:

```bash
mysql -u root -p < src/liane_library.sql
```

### 4. Set up environment variables
Copy the example file and fill in your credentials:

```bash
cp .env.example .env
```

Then edit `.env` with your actual values:

```
DB_USER=root
DB_PASSWORD=your_password_here
DB_HOST=localhost
DB_NAME=liane_library
```

> ⚠️ Never commit the `.env` file — it's already listed in `.gitignore`.

### 5. Run the app
```bash
streamlit run liane.py
```

The app will open in your browser at `http://localhost:8501`.

---

## Project Structure
```
LianesLibrary_Project/
├── liane.py              # Main Streamlit app
├── requirements.txt      # Python dependencies
├── .env.example          # Template for environment variables
├── .gitignore            # Excludes .env and other sensitive files
├── src/
│   └── liane_library.sql # MySQL schema + sample data
└── README.md
```

---

## Sample Data
The database comes pre-loaded with a few books and borrowers to get started:

**Books:** Der Alchemist, Der kleine Prinz, Homo Faber, Die unendliche Geschichte, Siddhartha

**Borrowers:** Liane (Admin), Max Mustermann, Erika Schmidt, Linus Torvalds

---


