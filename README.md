# Mod2 Week3 Assessment

## Setup
1. Fork this repository.
1. You can either work on your clone in GitHub, or open your clone in visual studio.

## Questions (10 Points Possible)

<img alt="erd_for_assessment" src="https://github.com/modelmapper/modelmapper/assets/11747682/60bebb3c-9faa-4f3e-ae0a-7df7dde06784">

[Citation for ERD](https://circle.visual-paradigm.com/hospital/)
1. Use the Doctors Office ERD above to answer the following questions:
    1. How many patients can each doctor have?
	    1: That is a many-to-one relationship. Many patients to one doctor. 
	    
    2. How many doctors can each patient have?
	    2: One doctor per patient. One-to-many relationship.
	    
    3. How would you describe the relationship between patients and tests? Be sure to use either one-to-one, one-to-many, or many-to-many in your answer.
	    3: The relationship is one patient to many tests, a one-to-many relationship.
	    
    4. What are the foreign keys in this diagram?
	    4: Doctor has a foreign key of doctor_id in the patients table, patient has a foreign key of patient_id in the tests table, and there are no foreign keys in the doctor table. in the tests table, and there are no foreign id in the doctor table. 
	    
    5. What is the primary key for the Tests table.
	    5: The primary key for the test table is id. 
	    
    6. What query would return the number of doctors who have a specialization in "pediatrics"?
  ```sql
  SELECT COUNT(specialization) FROM doctors WHERE specialization = 'pediatrics';
  ```
<br>

7. What does a join table do? Why would we need one?
	7: Joining two tables allows the programmer to select data from both tables and join them together to transform them into a bigger collection of data. You can specify whether you want more data from the left or right source by doing a left join, a right join, or including all data possible with a full join. 
	
8. What is a question that the following query helps answer?
	8: The query below helps answer the question Count the number of artists grouped by hometown. 

```sql
SELECT hometown, COUNT(name) FROM artists
GROUP BY hometown;
```

9. I'm trying to write a query to find the average age of all patients, but it's not working. How would you modify this query to get it to work as expected?
9:
```sql
SELECT age FROM AVERAGE(patients)
GROUP BY age;
```

10. How would you describe the difference between a `LEFT JOIN` and an `INNER JOIN`
	10: Left Join will include all data from the left source of the join statement while only taking the intersecting data from the right source. Inner Join will only take both intersecting data from each source on the left and right of the join statement.  
## Exercise (10 Points Possible)

Follow these steps to setup the assessment:
1. Create a new database named `flight_db` using pgAdmin.
2. Copy [this script](https://launch.turing.edu/module2/assessments/flight_db.txt) and paste it into the query tool to insert records into your database.
3. Run the following `SELECT` queries individually to get an understanding of the data:
> `SELECT * FROM airlines;`
> `SELECT * FROM flights;`

** If you need help setting up the database, reach out to an instructor! **

Please provide the QUERY (not the answer) that returns each of the following:
1. The flight numbers for all delayed flights (i.e. not on time).
``` sql
SELECT flight_number
FROM flights
WHERE on_time = false;
```
2. The count of delayed flights.
``` sql
SELECT COUNT(flight_number)
FROM flights
WHERE on_time = false;
```
1. The sum of prices for all flights arriving to Raleigh-Durham (`RDU`).
``` sql
SELECT SUM(price)
FROM flights
WHERE arrive_city = 'RDU';
```
1. The average price for all flights in the database.
``` sql
SELECT ROUND(AVG(price))
FROM flights;
-- added round to make output cleaner
```
3. The average price for all flights arriving to Raleigh-Durham.
``` sql
SELECT ROUND(AVG(price))
FROM flights
WHERE arrive_city = 'RDU';
-- added round to make output cleaner
```
5. The departure city and number of flights departing from each city.
``` sql
SELECT depart_city, COUNT(flight_number) 
FROM flights
GROUP BY depart_city;
```
7. The count of airlines in the database.
``` sql
SELECT COUNT(airline_name) AS "Count of Airlines"
FROM airlines;
```
9. The count of flights in the database.
``` sql
SELECT COUNT(flight_number) AS "Count of flights"
FROM flights;
```
11. The flight number, departure city, arrival city, price, and airline name of each flight. Do not return the airline ID number.
``` sql
SELECT 
flights.flight_number AS "Flight Numbers", 
flights.depart_city AS "Departure City",
flights.arrive_city AS "Arrival City", 
flights.price AS "Price of Flights", 
airlines.airline_name AS "Airline Name"
FROM flights LEFT JOIN airlines
ON airlines.id = flights.airline_id;
```
13. The airline name, flight number, and price of each flight on the Delta airline. (Assume that you do not know the ID number of the Delta airline. In a larger database, you would be expected to memorize ID numbers).
``` sql
SELECT 
airlines.airline_name AS "Air Line Name", 
flights.flight_number AS "Flight Numbers", 
flights.price AS "Price OF Flights"
FROM flights LEFT JOIN airlines
ON airlines.id = flights.airline_id
WHERE airline_name = 'Delta';
```

## Submission

Submit the Assessment Submission form linked in your cohort slack channel!

## Rubric

This assessment has a total of 20 Points. Earning 14 or more points is a pass and will indicate that you are progressing well with the material.

As a reminder, this assessment is for students and instructors to determine if there are any areas that need additional reinforcement!
