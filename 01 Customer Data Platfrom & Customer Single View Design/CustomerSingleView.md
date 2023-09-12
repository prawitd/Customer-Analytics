Customer Single View (CSV) is used in the hotel booking business to consolidate and centralize customer data from various sources. It provides a unified and comprehensive profile of each customer, allowing hotels to deliver personalized services and improve the overall guest experience. By having a complete view of a customer's interactions, preferences, and history with the hotel, staff can tailor their services, offer relevant promotions, and address specific needs, ultimately enhancing customer satisfaction and loyalty.

Below is a simplified sample dataset for hotel bookings:

CREATE TABLE HotelBookings (
    BookingID INT PRIMARY KEY,
    CustomerID INT,
    CheckInDate DATE,
    CheckOutDate DATE,
    RoomType VARCHAR(50),
    TotalAmount DECIMAL(10, 2),
    Status VARCHAR(20)
);

CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100),
    Phone VARCHAR(15),
    MembershipLevel VARCHAR(20)
);

INSERT INTO Customers (CustomerID, FirstName, LastName, Email, Phone, MembershipLevel)
VALUES
    (1, 'John', 'Doe', 'john@example.com', '+1-123-456-7890', 'Gold'),
    (2, 'Jane', 'Smith', 'jane@example.com', '+1-987-654-3210', 'Silver'),
    (3, 'Alice', 'Johnson', 'alice@example.com', '+1-555-555-5555', 'Platinum');

INSERT INTO HotelBookings (BookingID, CustomerID, CheckInDate, CheckOutDate, RoomType, TotalAmount, Status)
VALUES
    (101, 1, '2023-09-15', '2023-09-20', 'Deluxe', 600.00, 'Confirmed'),
    (102, 2, '2023-09-18', '2023-09-22', 'Standard', 400.00, 'Confirmed'),
    (103, 3, '2023-09-20', '2023-09-25', 'Suite', 900.00, 'Pending');

To create a Customer Single View (CSV) in SQL using data from hotel bookings, you can use SQL queries to join relevant tables and select the required customer information. Here's an example SQL query to retrieve customer details and their booking history:

SELECT
    c.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email,
    c.Phone,
    c.MembershipLevel,
    COUNT(b.BookingID) AS TotalBookings,
    MAX(b.CheckOutDate) AS LastCheckOutDate
FROM
    Customers c
LEFT JOIN
    HotelBookings b ON c.CustomerID = b.CustomerID
GROUP BY
    c.CustomerID, c.FirstName, c.LastName, c.Email, c.Phone, c.MembershipLevel;

This SQL query selects customer details from the "Customers" table and counts the number of bookings and retrieves the last check-out date using a LEFT JOIN with the "HotelBookings" table.
It groups the results by customer ID and other relevant customer information.
This query provides a basic CSV that includes customer information along with their booking history, which can be extended to include more specific data as needed for your use case.


