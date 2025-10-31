# Library Management System

**Course:** PROG211 - Object-Oriented Programming 1   
**Assignment:** Mini Library Management System

## Project Overview

A simple library management system built in Python using fundamental data structures (lists, dictionaries, and tuples) to manage books, members, and borrowing operations.

## Features

- **Book Management**: Add, search, update, and delete books
- **Member Management**: Register, update, and remove library members
- **Borrowing System**: Borrow and return books with limits
- **Genre Validation**: Uses tuples to enforce valid genres
- **Data Integrity**: Prevents deletion of books/members with active borrows

## Data Structures Used

### Lists
- `books[]` - Stores all book dictionaries
- `members[]` - Stores all member dictionaries
- `borrowed_books[]` - Tracks each member's borrowed books (inside member dictionary)

### Dictionaries
- **Book Dictionary**: Contains ISBN, title, author, genre, total_copies, available_copies
- **Member Dictionary**: Contains id, name, email, contact, borrowed_books

### Tuples
- `VALID_GENRES` - Immutable tuple containing valid genres: ("Fiction", "Non-Fiction", "Sci-Fi")

## File Structure

```
library-management-system/
│
├── operations.py          # Core functions (CRUD operations)
├── demo.py               # Demonstration script
├── tests.py              # Unit tests with assertions
├── UML_diagram.png       # Hand-drawn UML diagram
├── DesignRationale.pdf   # Design rationale document
└── README.md             # This file
```

. **Requirements**
   - Python 3.6 or higher
   - No external libraries required

## Running the Code

### 1. Run Demo Script
```bash
python demo.py
```
This demonstrates all system features including:
- Adding books and members
- Searching for books
- Borrowing and returning books
- Updating records
- Testing deletion restrictions

### 2. Run Unit Tests
```bash
python tests.py
```
Executes 8 unit tests covering:
- ISBN uniqueness validation
- Genre validation using tuples
- Borrow limit enforcement (max 3 books)
- Deletion restrictions
- Search functionality

### 3. Use Operations Directly
```python
from operations import *

# Add a book
add_book("978-1234567890", "Python Programming", "John Smith", "Non-Fiction", 5)

# Add a member
add_member("M001", "Alice Brown", "alice@email.com", "555-1234")

# Borrow a book
borrow_book("M001", "978-1234567890")

# Return a book
return_book("M001", "978-1234567890")
```

## Core Functions

### Book Operations
- `add_book(isbn, title, author, genre, total_copies)` - Add new book
- `search_books(search_term)` - Search by title or author
- `update_book(isbn, title, author, genre, total_copies)` - Update book details
- `delete_book(isbn)` - Delete book (only if no borrowed copies)

### Member Operations
- `add_member(member_id, name, email, contact)` - Register new member
- `update_member(member_id, name, email, contact)` - Update member details
- `delete_member(member_id)` - Remove member (only if no borrowed books)

### Borrow/Return Operations
- `borrow_book(member_id, isbn)` - Borrow book (max 3 per member)
- `return_book(member_id, isbn)` - Return borrowed book

### Display Functions
- `display_all_books()` - Show all books with availability
- `display_all_members()` - Show all registered members

## Business Rules

1. **ISBN Uniqueness**: Each book must have a unique ISBN
2. **Member ID Uniqueness**: Each member must have a unique ID
3. **Genre Validation**: Books can only have genres from the tuple: Fiction, Non-Fiction, or Sci-Fi
4. **Borrow Limit**: Members can borrow maximum 3 books at a time
5. **Deletion Protection**: 
   - Cannot delete books with borrowed copies
   - Cannot delete members with borrowed books
6. **Availability Tracking**: System tracks total copies and available copies separately

## Testing Strategy

The `tests.py` file includes 8 comprehensive tests using assertions:

1. ✓ Unique ISBN validation
2. ✓ Duplicate ISBN prevention
3. ✓ Genre validation using tuples
4. ✓ Borrow limit enforcement
5. ✓ Book deletion restriction
6. ✓ Member deletion restriction
7. ✓ Return functionality
8. ✓ Search functionality

## Assessment Criteria Compliance

| Criteria | Implementation | Marks |
|----------|---------------|-------|
| Dictionary | Books & Members stored as dictionaries | 20 |
| Lists | books[], members[], borrowed_books[] | 15 |
| Tuples | VALID_GENRES tuple for genre validation | 15 |
| UML Diagram/Documentation | UML diagram + Design Rationale PDF | 25 |
| Core Functionality | All CRUD + Borrow/Return operations | 25 |
| **Total** | | **100** |

## Example Usage

```python
# Example workflow
from operations import *

# Setup library
add_book("978-0-7475-3269-9", "Harry Potter", "J.K. Rowling", "Fiction", 5)
add_member("M001", "John Doe", "john@email.com", "123-456-7890")

# Member borrows book
result = borrow_book("M001", "978-0-7475-3269-9")
print(result)  # "Book 'Harry Potter' borrowed successfully by John Doe"

# Search for books
results = search_books("Harry")
for book in results:
    print(f"{book['title']} by {book['author']}")

# Return book
result = return_book("M001", "978-0-7475-3269-9")
print(result)  # "Book 'Harry Potter' returned successfully by John Doe"
```

## Documentation Files

### UML Diagram (UML_diagram.png)
Hand-drawn diagram showing:
- Data structure relationships (books, members, genres)
- Function interfaces
- Data flow between components

### Design Rationale (DesignRationale.pdf)
1-2 page document explaining:
- Why dictionaries were chosen for books and members
- Why lists were used for collections
- Why tuples were used for genre validation
- How the design meets all requirements
