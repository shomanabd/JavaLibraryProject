# Library Management System

## Overview
The Library Management System is a Java application designed to help school libraries efficiently track and manage their collections. The system allows librarians to manage books, CDs, library members (students and professors), and borrowing operations through an intuitive interface.

## Features
- **Item Management**
  - Add, search, update, and delete library items (Books and CDs)
  - Track copies available and borrowing status
  - Store detailed information about each item type

- **Member Management**
  - Register students and professors as library members
  - Maintain contact information and address details
  - Track items borrowed by each member

- **Borrowing System**
  - Check items in and out
  - Track due dates and borrowing history
  - Cancel borrowing and update due dates

- **Reporting**
  - Generate reports of all library items
  - View items borrowed by specific members
  - Sort items by borrowing frequency

- **File Operations**
  - Persist library data in random access files
  - Search, add, update, and delete items directly from files
  - Import items from files to the active library

## Project Structure
The system uses an object-oriented approach with the following key classes:

- **Library Items**
  - `LibraryItem`: Abstract base class for all library items with borrowing tracking
  - `Book`: Extends LibraryItem with author and ISBN information
  - `CD`: Extends LibraryItem with track number and composer details

- **Library Members**
  - `LibraryMember`: Abstract base class for all library users with borrowing methods
  - `Student`: Contains student-specific fields like student number and average mark (limited to 5 borrows)
  - `Professor`: Contains professor-specific fields like salary (no borrowing limit)

- **Supporting Classes**
  - `Address`: Manages address information in country@city@street@building@pobox format
  - `Name`: Handles name formatting for first, middle, and last names
  - `Borrow`: Manages borrowing dates and member information
  - `NewDate`: Custom date implementation for acquisition and due dates
  - `MyException`: Custom exception handling for library operations

- **Management Classes**
  - `Library`: Core class that manages collections of items and members
  - `LibraryFileManager`: Extends Library to handle file operations
  - `LibraryDriver`: Contains the main menu and user interface logic

## Class Details

### LibraryItem Class
- Abstract class implementing Comparable and Cloneable interfaces
- Core attributes: title, numberOfCopies, NumberOfborrow, borrow
- Comparison based on how often items have been borrowed
- Methods for cloning items and managing borrowing status

### LibraryMember Class
- Abstract class for managing member information and borrowing operations
- Core attributes: name, phoneNumber, emailAddress, dateOfBirth, address, LibraryItem (list), NumberOfborrowedItems
- Methods:
  - borrowLibraryItem: Allows members to borrow items (with student limitations)
  - removeLibraryItem: Returns borrowed items to the library
  - searchForItem: Locates items by title
  - updateItem: Updates due dates for borrowed items
  - memberIteamsReport: Generates a report of all borrowed items

### Student Class
- Extends LibraryMember with student-specific attributes
- Limited to borrowing maximum 5 items at a time
- Tracks studentNumber and averageMark
- Includes static IsEligibleToEnroll method to check if student has passing grades

### Professor Class
- Extends LibraryMember with professor-specific attributes
- No limit on number of borrowable items
- Tracks salary information

### Support Classes
- **Name**: Handles first, middle, and last name formatting
- **NewDate**: Custom date implementation with day, month, and year as strings
- **MyException**: Custom exception class for input validation

## Getting Started

### Prerequisites
- Java Development Kit (JDK) 8 or higher

### Installation
1. Clone the repository:
   ```
   git clone https://github.com/yourusername/library-management-system.git
   ```

2. Navigate to the project directory:
   ```
   cd library-management-system
   ```

3. Compile the project:
   ```
   javac Library/*.java
   ```

4. Run the application:
   ```
   java Library.LibraryDriver
   ```

### Usage Guide
The system provides a menu-driven interface with the following options:

1. **Add Library Item**: Add new books or CDs to the library
2. **Search Library Item**: Find items by title, author, or composer
3. **Delete Library Item**: Remove items from the library
4. **Update Library Item**: Modify item information
5. **Add Library Member**: Register new students or professors
6. **Search Library Member**: Find members by name
7. **Delete Library Member**: Remove members from the system
8. **Update Library Member**: Modify member information
9. **Borrow Library Item**: Check out items to members
10. **Library Item Borrow Cancellation**: Return items to the library
11. **Update Borrow Due Date**: Change the return deadline for items
12. **Print Member Items**: List all items borrowed by a specific member
13. **Print Library Report**: Generate a complete library inventory
14. **Write All Items To File**: Save library data to a file
15. **Search for Item in File**: Find items in the data file
16. **Delete Item in File**: Remove items from the data file
17. **Add Library Item to File**: Add new items directly to the file
18. **Update Library Item in File**: Modify items in the data file
19. **Add Item from File**: Import items from the file to the library
20. **Close the File**: Safely close the data file
21. **Exit**: Close the application

## Borrowing Rules
- Students are limited to borrowing a maximum of 5 items (books and CDs combined)
- Professors have no restriction on the number of items they can borrow
- The system prevents duplicate borrowing of the same item by a member
- Due dates are set during the borrowing process and can be updated later

## Data Format
- **Address Format**: `country@city@streetname@buildingname@pobox`
- **Item Storage**: Items are persisted in a random access file `item.dat`
- **Name Formats**: Supports both "FirstName LastName" and "FirstName MiddleName LastName"

## Error Handling
The system includes custom exception handling (MyException) to manage invalid input scenarios such as negative numbers of copies or borrows.

## Contributing
Contributions to improve the Library Management System are welcome. Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request


## Acknowledgments
- Developed as a project for school library management
- Implements object-oriented principles including inheritance and polymorphism
