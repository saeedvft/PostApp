# Postal Package Delivery System
![alt text]([https://github.com/[username]/[reponame]/blob/[branch]/image.jpg](https://github.com/saeedvft/PostApp/blob/main/Screenshots/Main-window.jpg)?raw=true)
## Introduction
In this project, you are tasked with implementing a postal package delivery system. The goal is to apply concepts from advanced programming and use C#, SQL Server, WPF, and Git to build this system. Additionally, one of the evaluation criteria is your ability to search and solve problems using the internet, a vital skill for any programmer.

## Tools
1. **WPF**:  
   Your project is a WPF application. In WPF projects, the frontend is designed using XAML. You can easily find information on how to create a WPF project by searching the internet. Video tutorials for learning this topic will also be provided.
   
2. **SQL Server**:  
   To store data persistently, you need to use a database. In this project, we will use SQL Server. You will also be provided with video tutorials for this. Alternatively, websites like W3Schools or other resources from a simple search can help you solve any issues.
   
3. **Git**:  
   Git is an essential tool for collaborative software development, helping with version control. You will be provided with video tutorials on Git as well. Create a GitHub account (if you don’t have one) and set up a repository named `AP_Project`, sharing it with the provided email addresses. After familiarizing yourself with Git, you should complete the following tasks for the project:
   
   - Create two main branches: `main` and `develop`.
   - The `develop` branch should be created from `main`. Each group member should create their own branch from `develop` and work on it. Once finished, merge your branch into `develop`, and later merge `develop` into `main`.

## Additional Notes
- You may implement the project as a console application, but doing so will result in only half of the total project score, even if fully functional. We strongly recommend using WPF.
- The SQL part of the project is optional. You can store the data in files instead of using SQL. However, due to the heavy interdependency of the data, using files might cause issues. We highly recommend using SQL Server.
- Your project should have a clean and visually appealing UI, which will be evaluated.
- You must implement **Exception Handling** throughout your application to ensure that it does not crash due to errors.
- For simplicity, you may use English labels and fields.
- Comment your code adequately and use meaningful variable, class, and function names to improve readability and make it easier for your teammates.
- You may seek help from your group or course assistants if you encounter issues.
- All group members must participate in the project, and this will be evaluated based on the registered commits and questions posed to the group on presentation day.
- Try to work on the project continuously to avoid last-minute issues.

## Project Scope

### 1. Types of Users
There are two types of users who can use this system:
- Postal office employees
- Customers (package senders)

### 2. Program Start
The application starts with a login screen where users can enter their username and password. The system will determine if the user is an employee or a customer based on the entered username. Employees will be directed to the employee panel, while customers will be directed to the customer panel.

There is a button on the login page labeled "Employee Registration" for employees who have not yet registered. Clicking this button will direct users to the employee registration page, where they will enter their full name, employee number, username, email, password, and password confirmation. After registration, they will be redirected to the login page to log in using the credentials they just created.

**Note**: Customer registration is only done by employees in the employee panel.

### 3. Employee Panel
After logging in, the employee is directed to a panel that includes a menu of tasks they can perform. Clicking on any menu item will take the employee to the corresponding page.

#### Employee Tasks
- **Registering Customers**:  
  Employees can register customers by entering their full name, national ID number, email, and phone number. A random username and password are generated for the customer and emailed to them. The customer can then use these credentials to log in to the customer panel.
  
- **Placing Orders**:  
  Employees enter the customer's national ID and click a button to check whether the customer is already registered. If not, they are redirected to the customer registration page. If the customer is already registered, the employee proceeds to the order placement page where they enter the following details:
    - Sender’s address
    - Recipient’s address
    - Package type (selectable: Object, Document, Fragile)
    - Checkbox to indicate if the package contains valuable items
    - Package weight in kilograms
    - Shipping method (selectable: Standard or Express)
    - Recipient’s contact number (optional)
    - A unique order ID generated sequentially

  After filling in these details, the employee clicks the "Calculate Shipping Cost" button, which will display a cost based on the entered information. The shipping cost is calculated as follows:
    - Base shipping fee: 10,000 Toman
    - Package type: no extra fee for objects, 1.5x for documents, 2x for fragile items
    - Valuable package: 2x fee
    - Weight over 0.5 kg: 1.2x for every additional 0.5 kg
    - Express shipping: 1.5x fee

  If the customer has enough balance in their wallet, the order is placed; otherwise, a message will be displayed about insufficient funds.

- **Order Report**:  
  Employees can filter and search through all registered orders based on:
    - Customer national ID
    - Package type
    - Shipping price
    - Package weight
    - Shipping method (Standard or Express)
  
  The search results will be saved in a CSV file, sorted by order registration date.

- **Order Details**:  
  Employees can enter an order ID to view the order’s details, including the current order status (Registered, Ready for Shipment, In Transit, Delivered). Employees can update the status, but once the order is marked as delivered, no further changes can be made.

- **Order Delivery Email**:  
  When an order is marked as delivered, an email is sent to the customer notifying them of the delivery.

- **Customer Feedback**:  
  Employees can view customer feedback for delivered orders.

### 4. Customer Panel
After logging in, the customer can access a menu of tasks they can perform.

#### Customer Tasks
- **Order Report**:  
  Similar to the employee's order report, but customers can only search through their own orders.
  
- **Order Details**:  
  Customers can enter their order ID to view details about the order. Customers can provide feedback once their order has been marked as delivered.

- **Wallet**:  
  Customers can view and recharge their wallet. After entering their card information and the amount, they can choose to receive a PDF receipt of the transaction.

- **Change Username and Password**:  
  Customers can update their username and password. If the entered username already exists, an error message will be displayed.

## Validation
All user inputs (both employee and customer) must be validated to ensure they fit within the database field constraints.

### 1. Regex Validations
- Names: minimum of 3 and maximum of 32 characters, consisting of only letters.
- Email: must follow the format `A@B.C`, where A and B are 3 to 32 characters and C is 2 to 3 characters.
- Phone numbers: must be exactly 11 digits and start with `09`.
- Employee password: 8 to 32 characters, including at least one uppercase letter, one lowercase letter, and one number.
- Customer password: exactly 8 digits, randomly generated.
- Username: starts with "user" followed by a 4-digit number.
- CVV: 3 to 4 digits.
- National ID: exactly 10 digits, starting with `00`.
- Employee ID: exactly 5 digits, with the third digit being `9`.

### 2. Card Validation
Some validations, like card expiration dates and numbers, require custom validation using the LUHN algorithm, which can be studied on Wikipedia.
