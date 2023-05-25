# Mod2 Week3 Assessment

## Setup
1. Fork this repository.
1. You can either work on your clone in GitHub, or open your clone in visual studio.

## Questions (10 Points Possible)

<img alt="erd_for_assessment" src="https://github.com/modelmapper/modelmapper/assets/11747682/60bebb3c-9faa-4f3e-ae0a-7df7dde06784">

[Citation for ERD](https://circle.visual-paradigm.com/hospital/)
1. Use the Doctors Office ERD above to answer the following questions:
    1. How many patients can each doctor have?
	    1: That is a many to one relationship. Many patients to one doctor. 
    2. How many doctors can each patient have?
	    2: One doctor per-patient. One to many relationship.
    3. How would you describe the relationship between patients and tests? Be sure to use either one-to-one, one-to-many, or many-to-many in your answer.
	    3: The relationship is one patient to many tests, one-to-many.
    4. What are the foreign keys in this diagram?
	    4: Doctor has a foreign key of doctor_id in the patients table , patient has a foreign key of patient_id in the tests table, and there are no foreign id in the doctor table. 
    5. What is the primary key for the Tests table.
	    5: The primary key for the test table is id. 
    6. What query would return the number of doctors who have a specialization in "pediatrics"?
	    6: SELECT COUNT(specialization) FROM doctors WHERE specialization = 'pediatrics';

<br>

7. What does a join table do? Why would we need one?
	7: Joining two tables allows the programmer to select data from both tables and join them together to transform them into a bigger collection of data. You can specify whether you want more data from the left or right source by doing a left join, a right join, or include all data possible with a full join. 
8. What is a question that the following query helps answer?
	8:. The query bellow helps answers the question Count the number of artists grouped by hometown. 

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
2. The count of delayed flights.
3. The sum of prices for all flights arriving to Raleigh-Durham (`RDU`).
4. The average price for all flights in the database.
5. The average price for all flights arriving to Raleigh-Durham.
6. The departure city and number of flights departing from each city.
7. The count of airlines in the database.
8. The count of flights in the database.
9. The flight number, departure city, arrival city, price, and airline name of each flight. Do not return the airline ID number.
10. The airline name, flight number, and price of each flight on the Delta airline. (Assume that you do not know the ID number of the Delta airline. In a larger database, you would be expected to memorize ID numbers).

## Submission

Submit the Assessment Submission form linked in your cohort slack channel!

## Rubric

This assessment has a total of 20 Points. Earning 14 or more points is a pass and will indicate that you are progressing well with the material.

As a reminder, this assessment is for students and instructors to determine if there are any areas that need additional reinforcement!
