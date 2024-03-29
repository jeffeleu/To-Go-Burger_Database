# To-Go Burger Database Management System

# Team Members:
Jeffery Liu

Rashedul Kabir

Donghyun Kim

Abdulbariu Olukoga

Wyeth Kong

# I. Business Scenario:
To-Go Burger is a fast food business that specializes in burgers and fries located in lower Manhattan. The company is currently facing a supplier management problem. Outdated supplier information, contact details, pricing, and delivery schedules are causing issues in ordering and pricing disputes. Additionally, there is confusion among employees regarding who oversees deliveries on specific days.

# II. ER Model using UML notation:

Relationships:

- One `<Customer>` may place zero to many `<Order>`.
- One `<Order>` must be placed by one and only one `<Customer>`.
- One `<Order>` may contain one to many `<Menu>`.
- One `<Menu>` may be included in one to many `<Order>`.
- One `<Menu>` may contain one to many `<Material>`.
- One `<Material>` may be included in one to many `<Menu>`.
- One `<Material>` must be supplied by one and only one `<Supplier>`.
- One `<Supplier>` may supply one to many `<Material>`.
- One `<Supplier>` must be requested by one and only one `<Employee>`.
- One `<Employee>` must request one and only one `<Supplier>`.
- One `<Employee>` must make one and only one `<Delivery>`.
- One `<Delivery>` must be assigned by one and only one `<Employee>`.

# III. Conversion to Relational Model:

Final Set of Relations:

Customer (CustomerID(key), First_Name, Last_Name, Home Address, Phone Number, Email, OrderID(fk))

Delivery (DeliveryID(key), EstimatedDateofArrival, Weight, Quantity, Status, SupplierID(fk), EmployeeID(fk))

Employees (EmployeeID(key), FirstName, LastName, PhoneNumber, DeliveryID(fk))

Material Information (Material ID#(key), Name, Description, Supplier Cost, Minimum Order Quantity, Lead Time, SupplierID(fk))

Menu (MenuID#(key), Name, Price, Material Quantity, Description, MaterialID(fk))

Order (OrderID(key), Date, Menu ID(fk), Order Quantity, Order Price, OrderType)

Supplier Information (Supplier ID#(key), Supplier Name, Address, CEO, Number, Email, EnployeeID(fk))

# IV. Normalization:
**Menu Table**:

First Normal Form:

Key: MenuID#
FD1: MenuID# → Name, Price

Second Normal Form:

Name_Table(Name, Price)
Name → Price
MenuID# → Name, Material Quantity, Description, MaterialID(fk)

Third Normal Form:

No transitive dependencies


**Delivery Table**:

First Normal Form:

Key: DeliveryID
FD1: DeliveryID → EstimatedDateofArrival, Weight, Quantity, Status, SupplierID(Fk), EmployeeID(fk)

Second Normal Form:

No Partial dependencies

Third Normal Form:

No transitive dependencies
(Similar normalization steps apply to other tables)

# V. Creating the Database Schema with Structured Query Language (SQL):

CREATE TABLE Customer

(

    CustomerID   VARCHAR(10) NOT NULL,
    First_Name    VARCHAR(35),
    Last_Name     VARCHAR(35),
    PhoneNumber  VARCHAR(15),
    Home Address      VARCHAR(35),
    Email     VARCHAR(12), 
	OrderID  VARCHAR(10) NOT NULL, 
    CONSTRAINT pk_customer
          PRIMARY KEY (CustomerID));

CREATE TABLE Delivery

(

    DeliveryID      VARCHAR(10) NOT NULL,
    EstimatedDateofArrival DATE,
    Weight FLOAT, 
    Quantity INTEGER,
    STATUS VARCHAR(10), 
    EmployeeID      VARCHAR(10) NOT NULL,
    SupplierID 	 	VARCHAR(10) NOT NULL,
    CONSTRAINT pk_Delivery
          PRIMARY KEY (DeliveryID)
);

CREATE TABLE SalonService
(

    ServiceID         VARCHAR(10) NOT NULL, 
    ServiceName       VARCHAR(35),
    ServiceDuration   INTEGER, 
    ServicePrice      FLOAT, 
    ServiceMaterials  VARCHAR(255),
    CONSTRAINT pk_salonservice
        PRIMARY KEY (ServiceID)
);

CREATE TABLE Employees 
(

    EmployeeID     VARCHAR(10) NOT NULL,
    FirstName      VARCHAR(35), 
    LastName       VARCHAR(25), 
    Phone Number        VARCHAR(45), 
    DeliverID       VARCHAR(12),
     CONSTRAINT pk_employee
       PRIMARY KEY (EmployeeID)
);




CREATE TABLE Material Information
( 

    MaterialID        VARCHAR(10) NOT NULL,
    Name       VARCHAR(35), 
    Description           VARCHAR(40), 
    Supplier Cost FLOAT, 
    SupplierID           VARCHAR(10) NOT NULL,
    Minimum Order Quantity INTEGER,
    Lead Time VARCHAR(10),
    CONSTRAINT pk_material 
        PRIMARY KEY (MaterialID)
);


CREATE TABLE Menu
(

    MenuID    VARCHAR(10) NOT NULL,
    Name     VARCHAR(35), 
    Price     FLOAT, 
    Material Quantity       VARCHAR(45), 
    Description VARCHAR(45)
    MaterialID      VARCHAR(12),
     CONSTRAINT pk_Menu
       PRIMARY KEY (MenuID)
);

CREATE TABLE Order
(

    OrderID    VARCHAR(10) NOT NULL,
    Date     DATE, 
    Order Quantity      VARCHAR(25), 
    Order Price        FLOAT,
    Order Type VARCHAR(25),
    Menu ID      VARCHAR(12),
     CONSTRAINT pk_order
       PRIMARY KEY (OrderID)
);
CREATE TABLE Supplier Information
(

    SupplierID#   VARCHAR(10) NOT NULL, 
    Order Quantity      VARCHAR(25),
    Supplier Name VARCHAR(25),
    Address VARCHAR(40),
    CEO VARCHAR(25),
    NUMBER VARCHAR(25),
    EMAIL VARCHAR(40),
    EmployeeID      VARCHAR(12),
     CONSTRAINT pk_supplier
       PRIMARY KEY (SupplierID)
);


# VI. Database Application:
Forms for inputting and deleting records are provided for customers, deliveries, employees, material information, orders, and supplier information.

Reports are available for querying and analyzing customer data, deliveries, employees, material information, menus, orders, and supplier information.

# VII. Conclusion:
For our project, we addressed a business scenario involving supplier management issues through an ER model, database normalization, SQL schema creation, and a user-friendly database application. Our efforts aimed at improving data accuracy, reliability, and efficiency for To-Go Burger. Continuous maintenance, optimization, and data archiving are suggested for future database enhancements.

