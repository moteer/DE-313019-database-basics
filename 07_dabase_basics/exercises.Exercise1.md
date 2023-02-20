## For the following tasks are used with the world database

(execute the world.sql script first in order to query it ;)

1. Get all Names of all the countries.
   
   ```
   SELECT Name FROM country
2. Get all Names and continents from all countries.
   ```
   SELECT Name, Continent FROM country

3. Get all the Information about your home country (filtering).
   ```
   SELECT *
   FROM country
   WHERE Name="Germany"
   
4. Get names of countries in Europe and in Africa.
   ```SELECT Name
   FROM country
   WHERE Continent="Europe"
   
5. How many countries are there in the world?
```
   SELECT count(*)
   FROM country
```

6. How many countries are there in Europe?
```
   SELECT count(*)
   FROM country
   WHERE Continent="Europe"
```

7. How can I rename the column header for the result? (use an alias).
```   
   SELECT count(*) AS TotalCountries
   FROM country
   WHERE Continent="Europe"
```

8. What is the total population of Europe?
```
   SELECT SUM(Population)
   FROM country
   WHERE Continent="Europe"
```

9. What is the average population by country in Europe?
```
   SELECT AVG(Population)
   FROM country
   WHERE Continent="Europe"
```

10. What is the smallest population of a country in the world?
```
SELECT MIN(Population)
FROM country
WHERE Continent="Europe"
```

11. What is the biggest population of a country in the world?
```
SELECT MAX(Population)
FROM country
WHERE Continent="Europe"
```

13. Display the number of countries for each continent.
```
SELECT Continent, count(*)
FROM country
GROUP BY Continent
-- Problem when ordering by a column that is an Enum
ORDER BY CAST(Continent AS CHAR)
```
14. Display the total population of each continent.
```
SELECT Continent, SUM(Population) AS "Total Population"
FROM country
GROUP BY Continent
ORDER BY CAST(Continent AS CHAR)
```
15. Show only the Regions which have more than 15 countries.
```
SELECT Region, COUNT(*) AS Total
FROM country
GROUP BY Region
HAVING COUNT(*)>15
ORDER BY Total DESC
```
16. Show only the Regions in Europe which have more than 5 countries.
```
SELECT Region, COUNT(*) AS Total
FROM country
WHERE Continent="Europe"
GROUP BY Region
HAVING COUNT(*)>5
ORDER BY Total DESC
```
17. How many countries are there in the world that have a population smaller than 10 million and that have gained independent before 1900?
```
SELECT count(*)
FROM country
WHERE population<10000000 AND IndepYear<1900
```
19. Same thing, but showing the names and the population of these countries, ordered by population (most populous first).
```
SELECT Name, Population
FROM country
WHERE population<10000000 AND IndepYear<1900
ORDER BY Population DESC
```
20. Display all countries which have "Arab" in their names.
```
SELECT Name
    FROM country
    WHERE Name LIKE "%Arab%"
```
20. Countries from Asia that have a population bigger than 100 million or a lifeexpectancy smaller than 65.
```
SELECT *
FROM country
WHERE Continent="Asia" AND (Population>100000000 OR LifeExpectancy<65)
```
21. Display all information for Portugal, Germany and Angola!
```
SELECT *
FROM country
WHERE Name IN ("Portugal", "Germany", "Angola")
```
23. Display all information for all the countries in the world, except Portugal, Brazil and Angola!
```
SELECT *
FROM country
WHERE Name NOT IN ("Portugal", "Brazil", "Angola")
-- Alternatives
-- WHERE Name!="Portugal" AND Name!="Brazil" AND Name!="Angola"
-- WHERE Name<>"Portugal" AND Name<>"Brazil" AND Name<>"Angola"
```
23. Calculate the Population density for every country in the world!
24. Display all the Hungarian :) cities.
25. Display the Greek cities that have a population bigger than 150000
26. Display all the cities from all the countries.
27. Display the official language for every country.
28. Display the name of each country and the name of the capital.