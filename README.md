# OIBSIP – Java Development Internship

Projects completed during the **Oasis Infobyte Java Development Internship**.

| Task | Project | Tech |
|------|---------|------|
| 1 | [Number Guessing Game](Java-Task1-NumberGuessingGame) | Java (console) |
| 2 | [Digital Library Management System](Java-Task2-DigitalLibrary) | Spring Boot, Thymeleaf, JPA, Spring Security, Maven |

---

## Task 1 – Number Guessing Game

A console-based game where the computer picks a random number and the player guesses it using "Too High!" and "Too Low!" hints until they win or run out of attempts.

### Features
- Random number generated at the start of every round
- Guess input through `Scanner`, with validation for invalid and out-of-range entries
- Feedback after every guess: **Too High!**, **Too Low!** or **Correct!**
- Attempt counter shown on every prompt, plus attempts left
- Maximum attempts limit; the game ends with **You Lost!** and reveals the number
- **Play Again** option after each round
- Score tracking across rounds, for example: `Round 2 - guessed in 5 attempts`
- Difficulty levels:

| Level  | Range | Attempts |
|--------|-------|----------|
| Easy   | 1–50  | 10 |
| Medium | 1–100 | 7  |
| Hard   | 1–200 | 5  |

### Concepts used
`Random`, `Scanner`, `while` loops, `if-else`, enums, classes and objects, `ArrayList`, `try-catch`

### How to run
```
cd Java-Task1-NumberGuessingGame
javac NumberGuessingGame.java
java NumberGuessingGame
```

---

## Task 2 – Digital Library Management System

A web-based library system with separate **Admin** and **User** roles. It manages the book catalogue, issuing and returning, fines, advance bookings and member queries.

### Admin features
- Secure login with access to all admin pages
- Add new books (title, author, ISBN, category, quantity)
- Edit or delete existing books
- View all issued books with due dates and overdue status
- View and manage members (block / unblock accounts)
- Fine management: view fines and mark them as paid
- Read messages sent through the contact form

### User features
- Registration and login (passwords stored as BCrypt hashes)
- Browse the catalogue by category
- Search for a book by title or author
- Issue a book (available quantity decreases, due date is recorded)
- Return a book (available quantity increases)
- Automatic fine for late returns: ₹5 per overdue day (14-day loan period)
- Advance booking: reserve a book that is currently issued to someone else
- Contact / query form that stores messages in the database

### Business rules
- Loan period is 14 days and the fine is ₹5 per overdue day
- A member with an unpaid fine cannot issue new books
- Free copies are held for members who reserved earlier
- A book with issue or reservation history cannot be deleted

### Tech stack
- **Language:** Java 17
- **Backend:** Spring Boot 3, Spring MVC, Spring Data JPA (Hibernate), Spring Security
- **Frontend:** Thymeleaf, HTML, CSS
- **Database:** H2 (file-based) for easy local setup; MySQL supported
- **Build tool:** Maven

### Project structure
```
Java-Task2-DigitalLibrary/
├── pom.xml
└── src/main/
    ├── java/com/library/
    │   ├── config/        Security configuration
    │   ├── controller/    Auth, User and Admin controllers
    │   ├── model/         User, Book, Loan, Reservation, ContactMessage
    │   ├── repository/    Spring Data JPA repositories
    │   └── service/       LibraryService (business rules)
    └── resources/
        ├── templates/     Thymeleaf pages (admin/ = admin panel)
        └── static/css/    Stylesheet
```

### Database design
| Table | Main columns |
|-------|--------------|
| users | id, name, email, password, role, enabled |
| book | id, title, author, isbn, category, total_quantity, available_quantity |
| loan | id, book_id, user_id, issue_date, due_date, return_date, fine_amount, fine_paid |
| reservation | id, book_id, user_id, reserved_on, status |
| contact_message | id, user_id, subject, message, created_at |

### How to run
1. Install JDK 17 or newer.
2. Open the `Java-Task2-DigitalLibrary` folder in VS Code and run `LibraryApplication.java`.
3. Open http://localhost:8080 in your browser.

**Admin login:** `admin@library.com` / `admin123`
Users can register from the login page.

To use MySQL instead of H2, edit `src/main/resources/application.properties` with your MySQL URL, username and password. Tables are created automatically.

---

## Author
**Anandshivam Burman Roy**
Final-year B.E. Computer Science and Engineering, St. Peter's Engineering College, Hyderabad
GitHub: [@lee-anand](https://github.com/lee-anand)

#oasisinfobyte #java #springboot #internship
