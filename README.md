# Book Management System

A comprehensive Java-based book management system that handles both physical and digital books with inventory management, customer purchases, and automated services.

## ✨ Features

### Core Functionality
- **Dual Book Types**: Support for both EBooks (PDF format) and Physical Paper Books and Demo
- **Inventory Management**: Real-time tracking of book quantities and availability
- **Customer Management**: Customer profiles with purchase history and wallet system
- **Automated Services**: Email delivery for EBooks and shipping for physical books
- **Admin Controls**: Administrative functions for adding books and managing inventory
- **Outdated Book Cleanup**: Automatic removal of books older than specified criteria

### Advanced Features
- **Quantity Validation**: Prevents over-purchasing and negative inventory
- **Service Integration**: Automated email and shipping service dispatch
- **Error Handling**: Comprehensive error messages for failed operations
- **Inventory Display**: Visual representation of current stock levels


## 📚 Classes Overview

### Core Classes

#### `Book` (Abstract)
Base class for all book types with common properties:
- `ISBN`: Unique identifier
- `title`: Book title
- `publishedAt`: Publication year
- `price`: Book price
- `send()`: Abstract method for delivery

#### `EBook` extends `Book`
Digital book implementation:
- `format`: File format (PDF, EPUB, etc.)
- Uses `MailService` for delivery
- Instant delivery via email

#### `PaperBook` extends `Book`
Physical book implementation:
- `copies`: Physical inventory count
- Uses `ShippingService` for delivery
- Requires physical shipping
- 
#### `DemoBook` extends `Book`

### Management Classes

#### `Admin`
Administrative operations:
- `AddBook(Book book, int quantity)`: Add books to inventory
- `returnAndRemoveOLDs()`: Remove outdated books
  
#### `Customer`
Customer operations:
- `buyBook(String ISBN, int quantity)`: Purchase books
- `balance`: Customer wallet balance
  
#### `Inventory` (Static)
Centralized inventory management:
- `addBook()`: Add books to inventory
- `decreaseQuantity()`: Reduce stock levels
- `getBookAvailability()`: Check stock levels
- `ShowInventory()`: Display current inventory
  
### Service Classes

#### `MailService` implements `IService`
Email delivery service for digital books:
- `fire(Book book, String email)`: Send book via email

#### `ShippingService` implements `IService`
Physical shipping service for paper books:
- `fire(Book book, String address)`: Ship book to address
