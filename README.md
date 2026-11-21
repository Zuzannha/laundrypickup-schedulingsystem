### LaundryGoGoGo: Your Laundry, Our Priority!

**Description:** The LaundryGoGoGo is a Java-based application designed to make laundry services more convenient, organized, and efficient. It allows customers to schedule their laundry pickups and deliveries by providing their personal information, selecting a laundry service, entering the weight of their laundry, and choosing their preferred pickup and delivery dates. The system offers five laundry services: Wash & Fold, Wash & Iron, Dry Cleaning, Comforters & Bedding, and Stain Removal.

### Object-Oriented Programming Concepts Applied

The following are the detailed documentation of how the OOP principal were used throughout the program:

### Encapsulation
**Where:** LaundryService, Customer, and LaundryOrder classes.

Encapsulation is demonstrated by using private variables and accessing them through public getter methods.
```java
class Customer {
    private String customerName;

    public Customer(String customerName) {
        this.customerName = customerName;
    }

    public String getCustomerName() {
        return customerName;
    }
}
```
The variable customerName is private, meaning it cannot be directly accessed outside the class. The getCustomerName() method allows other classes to access its value.

Encapsulation is used to protect important customer and order information from being accessed or changed directly by other parts of the program. It provides controlled access to the data and helps maintain the organization and reliability of the system.

### Inheritance
Inheritance allows one class to acquire the properties and methods of another class. It helps avoid writing the same code repeatedly.

```java
class WashFold extends LaundryService {

    public WashFold() {
        super("Wash & Fold", 35.00);
    }

    @Override
    public double calculateCost(double weight) {
        return getPricePerKg() * weight;
    }
}
```
Other examples:

```java
class WashIron extends LaundryService
class DryCleaning extends LaundryService
class Bedding extends LaundryService
class StainRemoval extends LaundryService
```
In this code, LaundryService serves as the parent class, while WashFold, WashIron, DryCleaning, Bedding, and StainRemoval are the child classes.

The child classes inherit the common properties and methods from LaundryService, such as the service name and price per kilogram.

The keyword extends establishes the inheritance relationship, while super() calls the constructor of the parent class to initialize the service name and price.

Inheritance is used because the five laundry services share common information, such as their service names and prices. Instead of creating separate variables and methods for every service, the program places their common features in one parent class and allows each child class to inherit them.


### Abstraction
Abstraction hides unnecessary implementation details and focuses on the essential features and functions that a class should provide.

```java
abstract class LaundryService {

    private String serviceName;
    private double pricePerKg;

    public LaundryService(String serviceName, double pricePerKg) {
        this.serviceName = serviceName;
        this.pricePerKg = pricePerKg;
    }

    public String getServiceName() {
        return serviceName;
    }

    public double getPricePerKg() {
        return pricePerKg;
    }

    public abstract double calculateCost(double weight);
}
```
In this code, LaundryService is declared as an abstract class using the keyword abstract. This means it cannot be directly instantiated to create an object.

Instead, it serves as a general template for the different laundry services. It defines common properties, such as serviceName and pricePerKg, and requires its child classes to provide an implementation of the abstract calculateCost() method.

The parent class establishes what every laundry service should have without requiring the user to know the internal implementation of each service.

Abstraction is used to create a common structure for all laundry services. It ensures that every service follows the same basic design while allowing each child class to provide its own implementation of the required method.

### Polymorphism
Polymorphism allows different classes to use the same method name but provide their own implementation of that method.

```java
@Override
public double calculateCost(double weight) {
    return getPricePerKg() * weight;
}

class WashFold extends LaundryService
class WashIron extends LaundryService
class DryCleaning extends LaundryService
class Bedding extends LaundryService
class StainRemoval extends LaundryService

LaundryService selectedService =
        services.get(serviceChoice - 1);

public double getBaseCost() {
    return service.calculateCost(weight);
}
```
In this code, the calculateCost() method is overridden by each child class. Although all five classes use the same method name and calculation formula, each service has a different price per kilogram.

When a customer selects a laundry service, the program uses the corresponding service object's implementation of calculateCost() to calculate the correct amount.

Polymorphism is used to allow the system to calculate different laundry service costs using one common method. It makes the program more flexible because additional laundry services can have their own implementations without changing the overall order calculation process.

### Program Structure

Main Class

```java
- Starting the program
- Initializing available laundry services
- Displaying the main menu
- Accepting user selections
- Managing the overall program execution
```
LaundryService  Class

```java
ROLE: Main controller of the application. Handles:
- Starting the program
- Initializing available laundry services
- Displaying the main menu
- Accepting user selections
- Managing the overall program execution

RESPONSIBILITIES:
• main()
• initializeServices()
• displayMenu()
• createOrder()
• displayServices()
• displayAllOrders()
• readInt()
• readDouble()
• readDate()

RELATIONSHIPS:
- Uses LaundryService objects
- Creates Customer objects
- Creates LaundryOrder objects
- Stores services and orders using ArrayLists
```
WashFold Class

```java
ROLE: Represents the Wash & Fold laundry service.

DATA:
- Service name: Wash & Fold
- Price: PHP 35.00 per kg

RESPONSIBILITIES:
• Initialize the Wash & Fold service
• Calculate the laundry cost based on weight
• Override calculateCost()

RELATIONSHIPS:
- Extends LaundryService
```
WashIron Class

```java
ROLE: Represents the Wash & Iron laundry service.

DATA:
- Service name: Wash & Iron
- Price: PHP 55.00 per kg

RESPONSIBILITIES:
• Initialize the Wash & Iron service
• Calculate the laundry cost based on weight
• Override calculateCost()

RELATIONSHIPS:
- Extends LaundryService
```
DryCleaning Class

```java
ROLE: Represents the Dry Cleaning laundry service.

DATA:
- Service name: Dry Cleaning
- Price: PHP 120.00 per kg

RESPONSIBILITIES:
• Initialize the Dry Cleaning service
• Calculate the laundry cost based on weight
• Override calculateCost()

RELATIONSHIPS:
- Extends LaundryService
```
Bedding Class

```java
ROLE: Represents the Comforters & Bedding laundry service.

DATA:
- Service name: Comforters & Bedding
- Price: PHP 80.00 per kg

RESPONSIBILITIES:
• Initialize the Comforters & Bedding service
• Calculate the laundry cost based on weight
• Override calculateCost()

RELATIONSHIPS:
- Extends LaundryService
```
StainRemoval Class

```java
ROLE: Represents the Stain Removal laundry service.

DATA:
- Service name: Stain Removal
- Price: PHP 95.00 per kg

RESPONSIBILITIES:
• Initialize the Stain Removal service
• Calculate the laundry cost based on weight
• Override calculateCost()

RELATIONSHIPS:
- Extends LaundryService
```
Customer Class

```java
ROLE: Stores the customer's personal information.

DATA:
- customerName

RESPONSIBILITIES:
• Initialize customer information
• Store the customer's name
• Provide getCustomerName()

RELATIONSHIPS:
- Used by LaundryOrder to identify the customer
- Created by the Main class
```
LaundryOrder Class

```java
ROLE: Manages the details and calculations of each
laundry order.

DATA:
- Customer information
- Selected laundry service
- Laundry weight
- Pickup date
- Delivery date
- Express service status

RESPONSIBILITIES:
• Store laundry order information
• getBaseCost()
• getExpressFee()
• getTotalCost()
• displayReceipt()
• Calculate the base laundry cost
• Calculate the additional 20% express fee
• Generate the laundry receipt

RELATIONSHIPS:
- Has-a Customer
- Has-a LaundryService
- Created and managed by the Main class
```
### How to Run the Program

### PREREQUISITES
1. Before running the program, make sure the Java JDK 17 or later is installed.
2. Go to the GitHub repository.
3. Click the green Code button and Download ZIP.
4. Extract the ZIP file to a folder (e.g., C:\Users<YourName><ZIPfile>).

AFTERWARDS, COMPILE THE PROGRAM:
5. Open VS Code or another compiler.
6. Select File, then choose Open Folder and choose the project folder.
7. Open Main.java and click the Run button or open a New Terminal and type java Main.java.

### TO NAVIGATE THE PROGRAM:
**1. Main Menu** 
