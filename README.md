# PROJECT PHASE-4 

1. Hire employee:
 
        INSERT INTO Flight_Employee 
        (Emp_id, F_name, M_name, L_name, Jobtype, Salary, Bdate,        Works_For, ManagerID) 
        VALUES (input values);

2. Fire Employee:
   
        DELETE FROM Flight_Employee WHERE Emp_id = 'input';

3. Promote an Employee
   
        UPDATE Flight_Employee SET Salary = 'input' WHERE Emp_id='input';

4. Add Airport
   
        INSERT INTO Airport (Ap_name, City, Country) VALUES (input values);
    
5. Delete Airport
   
        DELETE FROM Airport WHERE Ap_name = 'input';

6. Get details of all Employees working at an Airport
   
        SELECT Emp_id, F_name, M_name, L_name, Phone_No 
        FROM Flight_Employee 
        JOIN Employee_Phone ON Flight_Employee.Emp_id = Employee_Phone.PID 
        JOIN Airline ON Flight_Employee.Works_For = Airline.Airline_ID
        JOIN Operates ON Airline.Airline_ID = Operates.AirlineID
        WHERE Operates.AirportID = 'input';
        

7. Get Airlines operating at a specific airport 
   
        SELECT Airline.Airline_ID, Airline.Airline_name 
        FROM Airline 
        JOIN Operates ON Airline.Airline_ID = Operates.AirlineID 
        WHERE Operates.AirportID = 'input';

8.  Get average salary of all employees at a specific airport
   
        SELECT AVG(Salary) AS Average_Salary
        FROM Flight_Employee 
        JOIN Airline ON Flight_Employee.Works_For = Airline.Airline_ID
        JOIN Operates ON Airline.Airline_ID = Operates.AirlineID
        WHERE Operates.AirportID = 'input';

9. Get number of flights operated by each airline at a specific airport
        
        SELECT Airline.Airline_name, COUNT(Flight.Flight_code) AS Flight_Count
        FROM Flight
        JOIN Flight_Employee ON Flight.Pilot = Flight_Employee.Emp_id
        JOIN Airline ON Flight_Employee.Works_For = Airline.Airline_ID
        JOIN Operates ON Airline.Airline_ID = Operates.AirlineID
        WHERE Operates.AirportID = 'input'
        GROUP BY Airline.Airline_name;

10. Get total baggage weight for each passenger on a specific flight
    
        SELECT Passenger.F_name, Passenger.M_name, Passenger.L_name, SUM(Baggage.Weight) AS Total_Weight
        FROM Passenger
        JOIN Baggage ON Passenger.PID = Baggage.BelongsTo
        WHERE Passenger.BoardingFlight = 'input'
        GROUP BY Passenger.PID;


11. Search Passenger by Name
    
        SELECT PID, F_name, M_name, L_name, Bdate, BoardingFlight
        FROM Passenger
        WHERE F_name LIKE 'input' OR M_name LIKE 'input' OR L_name LIKE 'input';

12. Delete Airline
    
        DELETE FROM Airline WHERE Airline_ID = 'input';

13. Delete Baggage
    
        DELETE FROM Baggage WHERE BaggageId = 'input' AND BelongsTo = 'input';

14. Logout

        To exit the program
Here input is the user inputs.
