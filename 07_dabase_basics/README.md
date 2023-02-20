
# Basic sql statements on worlds database

switch to use database world
```
USE world;
```

Display one table content
```
SELECT * FROM country;
```

Aggregation function COUNT and ALIASING
```
SELECT CountryCode, COUNT(CountryCode) AS "Total number of languages"
FROM countrylanguage
GROUP by CountryCode;
```

Ordering results with ORDER BY
```
SELECT * 
FROM city
ORDER BY name ASC;
```

Using the WHERE clause on countryCode
```
SELECT name, population 
FROM city
WHERE countryCode="PRT"
ORDER by population DESC
LIMIT 1;
```
Returns grom which countries we don't have any information about LifeExpectancy. 
```
SELECT name, LifeExpectancy 
FROM country
WHERE LifeExpectancy IS NOT NULL
ORDER BY LifeExpectancy ASC
LIMIT 1;
```

Displays everything about Portugal, Brazil and Hungary
```
SELECT *
FROM country
WHERE name NOT IN ("Portugal", "Brazil", "Hungary");
```

Displays the city name and population for Greece and Hungary
```
    SELECT city.name, city.Population
    FROM country JOIN city
    ON country.code = city.countryCode
    WHERE country.name IN ("Greece", "Hungary");
```
Shows the official language for every country
```
    SELECT country.name, Language
    FROM country join countrylanguage
    ON country.Code = countrylanguage.CountryCode
    WHERE IsOfficial = "T" AND
    country.Name IN ("Greece", "Hungary");
```

CRUD Operations
INSERT
```
INSERT INTO club (name, points) 
VALUES ('Test2',2);
```

UPDATE
```
UPDATE club
SET name = "Better name", points = 4
WHERE id = 100; 
```

DELETE
```
DELETE FROM club 
WHERE id=100;
```


