# Base-de-Datos.-SQL



| Declarativo                          | Imperativo |
| ------------------------------------ | ---------- |
| que                                  | como       |
| number.filter (number>3)             | for()      |
| (number =>)                          |            |
| var numbers = [1,2,3,4,5]            |            |
| var result = number.filter(x => x>3) |            |

# SQL
## SELECT

> SELECT Empleados.Nombre    
> FROM Empleados       
>> WHERE (Genero = “M” AND Hijos =0)     
>>>OR (Genero =”F” AND Hijos>0);     

Al finalizar se coloca un punto y coma, no en medio del codigo.     
En esta cnsulta se buscan los chicos sin hijos o las chicas con al menos un hijo.          
>SELECT           
selecciona el atributo que nos va a mostrar de la tabla de datos que vamos a utilizar.        
>FROM     
selecciona la tabla de datos para realizar la búsqueda.     
-----------------------------------------------------

Con esta búsqueda se muestran todos los países que tengan la primera letra en orden alfabético mayor que Cuba.    
>FROM  
es una tabla de datos muy amplia.          
Se utilizan comillas simples.        

>SELECT       
dos valores separados por una coma.  

Se nos mostrará el nombre y la poblacion de los países alfabéticamente después que Cuba.         

>SELECT name,population        
FROM world        
 >> WHERE name >'Cuba';       

| world_name         | world_populat.. |
| ------------------ | --------------- |
| Cyprus             | 865878          |
| Czech Republic     | 10517400        |
| Denmark            | 5634437         |
| Djibouti           | 886000          |
| Dominica           | 71293           |
| Dominican Republic | 9445281         |
| Ecuador            | 15774200        |
| Egypt              | 86736900        |
| El Salvador        | 6384000         |
| Equatorial Guinea  | 1622000         |
| Eritrea            | 6536000         |
| Estonia            | 1315819         |
| Ethiopia           | 87952991        |
| Fiji               | 858038          |
| ...                |                 |

-------------------------------------------

En esta búsqueda se ordenan los países según la poblacion con letra posterior a C en orden de mayor a menor.    
> sustituímos DESC por ASC para ordenarlo de menor a mayor.    

> SELECT    
    nos muestra el nombre y la población del país.     

> ORDER BY  
> se utiliza para indicar comó queremos ordenar. En este caso se ordena según la población y de forma DESC.

>SELECT name,population    
FROM world   
 >> WHERE name >'Cuba'    
>>>ORDER BY population DESC;   
 
| world_name    | world_populat |
| ------------- | ------------- |
| India         | 1246160000    |
| United States | 318320000     |
| Indonesia     | 252164800     |
| Pakistan      | 188020000     |
| Nigeria       | 178517000     |
| Russia        | 146000000     |
| Japan         | 127090000     |
| Mexico        | 119713203     |
| Philippines   | 99804200      |
| Vietnam       | 89708900      |
| Ethiopia      | 87952991      |
| Egypt         | 86736900      |
| Germany       | 80716000      |
| Iran          | 77552000      |
| ...           |               |

-----------------------------------------------


>SELECT name,population   
FROM world    
>>  WHERE name >'A'    
>>>ORDER BY population ASC    
LIMIT 1,10;    

>LIMIT
Limita a los 10 primeros valores  de la búsqueda. En este caso está ordenado por poblacion de menor a mayor. 



| world_name            | world_populat |
| --------------------- | ------------- |
| Nauru                 | 9945          |
| Tuvalu                | 11323         |
| Palau                 | 20901         |
| San Marino            | 32637         |
| Monaco                | 36950         |
| Liechtenstein         | 37132         |
| Saint Kitts and Nevis | 55000         |
| Marshall Islands      | 56086         |
| Dominica              | 71293         |
| Andorra               | 76098         |
--------------------------------------------------------

>SELECT name, population  
FROM world   
 >> WHERE name IN ('Sweden', 'Norway', 'Denmark');   
  
            (en negrita, se encuentra todo el predicado.)    
Sacará la población de los nombres que hemos puesto. La muestra según el orden en la que las encuentra. 
>IN
 es para utilizar esos nombres separados por comas.    

----------------------------
### **BETWEEN -__AND __**
>SELECT name, area   
FROM world  
>>WHERE area BETWEEN 250000 AND 300000;

| name         | area   |
| ------------ | ------ |
| Burkina Faso | 272967 |
| Ecuador      | 276841 |
| Gabon        | 267668 |
| New Zealand  | 270467 |

En esta consulta se utiliza:
> BETWEEN -- AND --  
> para establecer dos valores entre los que realizar la consulta incluidos los escritos
-------------------------------------------------------------  

>SELECT name  
 FROM world  
 >> WHERE name LIKE 'F%';

### **LIKE**  
Se utiliza para buscar una variable, es decir, busca la letra F% (el % se coloca para posicionar la ubicación de la letra).   
En este caso nos mostrará los países en los que su primera letra sea una F.

|name|
|--|
|Fiji|
|Finland|
|France|

1-.
You can use WHERE name LIKE 'B%' to find the countries that start with "B".
The % is a wild-card it can match any characters.  
  
>SELECT name  
 FROM world  
 >> WHERE name LIKE 'B%';

|name|
|--|
|Bahamas|
|Bahrain|
|Bangladesh|
|Barbados|
|Belarus|
|Belgium|
|Belize|
|Benin|
|Bhutan|
|Bolivia|
|Bosnia and Herzegovina|
|Botswana|
|Brazil|
|Brunei|
|Bulgaria|
|Burkina Faso|
|Burundi|


2-.  
> SELECT name   
> FROM world  
> >WHERE name LIKE '%man%'

|name|
|--|
|Oman|
|Germany|
|Romania|

En este caso los %% sirven para indicar que queremos consultar solo los nombres de países en los que se encuentre la palabra **man**.

3-. Find the countries that end with y.
> SELECT name   
> FROM world  
> >WHERE name LIKE '%y';  

|name|
|--|
|Turkey|
|Germany|
|Hungary|
|Italy|
|Norway|
|Vatican City|
|Paraguay|
|Uruguay|

4-.
Luxembourg has an x - so does one other country. List them both.
Find the countries that contain the letter x.
>SELECT name    
FROM world  
>>WHERE name LIKE '%x%';

|name|
|--|
|Luxembourg|
|Mexico|

5-. 
Iceland, Switzerland end with land - but are there others?
Find the countries that end with land.
>SELECT name   
FROM world  
>>WHERE name LIKE '%land';


|name|
|--|
|Swaziland|
|Thailand|
|Finland|
|Iceland|

**%**  
Lo colocamos al final principio de la parte que queremos encontrar.  

6-. 
Columbia starts with a C and ends with ia - there are two more like this.
Find the countries that **start with C and end with ia**.

>SELECT name   
FROM world  
>>WHERE name LIKE 'C%ia';

>La búsqueda sustituirá el % por el sinfín de letras que existan para mostrar los nombres reales de los países que comiencen por C y terminen por ia.

|name|
|--|
|Cambodia|
|Colombia|
|Croatia|



7-. Greece has a double e - who has a double o?
Find the country that **has oo** in the name

>SELECT name  
 FROM world  
 >> WHERE name LIKE '%oo%';


|name|
|--|
|Cameroon|

>Utilizamos los %% con la parte exacta que queremos encontrar dentro.   
  
  
  
8-. Bahamas has three a - who else?
Find the countries that have **three or more a** in the name

>SELECT name   
FROM world  
>>WHERE name LIKE **'%a%a%a%'**;

>En este caso un poco especial, quermeos encontrar los nombres de los países en los que existan más de 3 letras, aes. Para realizarlos utilizamos la teoría del LIKe con %. Es muy importante que se coloquen antes y despúes de cada letra para que se entienda que es solo eso lo que se quiere buscar.

|name|
|--|
|Central African Republic|
|Equatorial Guinea|
|Madagascar|
|Mauritania|
|Tanzania|
|Afghanistan|
|Azerbaijan|


### **Guión bajo: _**
9-. India and Angola have an n as the second character. You can use the underscore as a single character wildcard.
SELECT name FROM world
 WHERE name LIKE '_n%'
ORDER BY name
 
Find the countries that have "t" as the second character.

>SELECT name   
FROM world
>>WHERE name LIKE '_t%'  
>>>ORDER BY name;

> Aparece un nuevo elemento: _. Se utiliza para indicar los caracteres anteriores o posteriores, es decir, con _ podemos indicarle que es la segunda letra del nombre. La consulta sustituirá _ por un caracter. 

|name|
|--|
|Ethiopia|
|Italy|



10-. Cuba and Togo have four characters names.
Find the countries that have exactly **four characters.**

>SELECT name   
FROM world  
>>WHERE name LIKE '____';


|name|
|--|
|Chad|
|Mali|
|Togo|
|Iran|
|Iraq|
|Laos|
|Oman|

>Para realizar la conuslta colocamos en el LIKE el número de _ según los caracteres que queramos que tenga el nombre del país.


13-.

>SELECT name  
   FROM world  
>>WHERE name LIKE '%a%'  
  >>>AND name LIKE '%e%'  
AND name LIKE '%i%'  
AND name LIKE '%o%'  
AND name LIKE '%u%'  
;

**AND**
Nos vale para añadir contenido al predicado de la búsqueda. Estamos buscando los países que tengan a, e, i, o y u en su nombre.   
**OR**  
Utilizaremos OR caundo queramos indicar que los caracteres a buscar son opcionales. 

|name|
|--|
|Congo|
|Democratic Republic of Equatorial Guinea|
|Mozambique|
|Dominican Republic|


-------------------------------------------------------
-------------------------------------------------------
## **JOIN**

### MORE JOIN OPERATIONS

List the films where the yr is 1962 [Show id, title] 

>SELECT id, title  
 FROM movie  
 >>WHERE yr=1962;

| id   | title                            |
| ---- | -------------------------------- |
| 121  | To Kill a Mockingbird            |
| 479  | Dr. No                           |
| 1082 | Music Man, The                   |
| 1496 | What Ever Happened to Baby Jane? |
| 1751 | Cape Fear                        |

>**=**   
Utilizaremos el igual a para mostrar los valores exactos de las consultas. Se convierte entonces la búsqueda en una expresión regular.   
De forma predeterminada están ordenadas por el id de menor a mayor, para cambiarlo es necesario utilizar ORDER BY.

2-.
Give year of 'Citizen Kane'.  
>SELECT movie.yr  
 FROM movie   
>>WHERE movie.title = 'Citizen Kane';

Aquí utilizaremos una forma compuesta para hacer referencia al nombre, es decir, buscaremos CItizen Kane en movie y dentro en título. **SELECT** lo empleamos para escoger el **valor a mostrar**. 

|yr|
|--|
|1941|

>Nos muestra el año exacto en la que se lanzó la película.

3-.
List all of the Star Trek movies, include the **id, title and yr** (all of these movies include the words Star Trek in the title). Order results by year.  

>SELECT movie.id, movie.title, movie.yr   
FROM movie   
>>WHERE movie.title LIKE '%Star Trek%';


da error


>SELECT movie.id, movie.title, movie.yr  
FROM movie  
>>WHERE (PREDICADO) movie.title LIKE '%Star Trek%'  
ORDER BY movie.yr ASC;  

En ORDER BY especificamos por el tipo de datos que quermeos ordenar: año de lanzamiento de la película.

| id  | title                                  | yr   |
| --- | -------------------------------------- | ---- |
| 402 | Star Trek: The Motion Picture          | 1979 |
| 209 | Star Trek: The Wrath of Khan           | 1982 |
| 438 | Star Trek III: The Search for Spock    | 1984 |
| 349 | Star Trek IV: The Voyage Home          | 1986 |
| 472 | Star Trek V: The Final Frontier        | 1989 |
| 410 | Star Trek VI: The Undiscovered Country | 1991 |
| 280 | Star Trek: Generations                 | 1994 |
| 68  | Star Trek: First Contact               | 1996 |
| 252 | Star Trek: Insurrection                | 1998 |


4.
What id number does the actor 'Glenn Close' have?

>SELECT actor.id  
FROM actor  
>>WHERE actor.name = 'Glenn Close';   

    LIKE: sería igualmente válido aunque podemos correr el riesgo de que exista Glenn Close 2, etc...

 En este ejercicio se pueden utilizar ambos, con el % es para LIKE
Con el **LIKE ‘The%’ es una expresión regular**, es decir, el % no está incluido en la frase pero quiere decir que hay n caracteres después del %. Si usamos **= ‘The%’ es una cadena** por lo que el **%** está **incluído** en el nombre.


|id|
|--|
|104|

5-. What is the id of the film 'Casablanca'
>SELECT movie.id  
FROM movie  
>>WHERE movie.title **LIKE/=**  'Casablanca' ;  
        
    LIKE: sería igualmente válido aunque podemos correr el riesgo de que exista Casablanca 2, etc...

|id|
|--|
|27|


6.Obtain the cast list for 'Casablanca'.  
    What is a cast list?
    The cast list is the names of the actors who were in the movie.
Use movieid=11768, (or whatever value you got from the previous question).

>SELECT actor.name  
FROM actor JOIN casting ON actor.id = casting.actorid  
>>WHERE casting.movieid = 27;

### **JOIN**
>Utilizamos JOIn para enlazar datos de una tabla con otra, es decir, en ste ejercicio tenemos actor, movie y casting. La única forma de llegar desde movie hasta actor es pasando por casting entonces, en este caso, se le indica que queremos ir desde actor **JOIN casting ON** se utiliza para relacionar terminos. Estamos relacionando actor.id = casting.actorid y despues, lo que hace la consulta es buscar qué peliculas tienen el movie.id=27 para mostrar sus actores.  

|name|
|--|
|Humphrey Bogart|
|Ingrid Bergman|
|Claude Rains|
|Peter Lorre|
|Paul Henreid|
|John Qualen|
|Curt Bois|
|Conrad Veidt|
|Madeleine LeBeau|



Si no sabemos el id de la pelicula hyacemos esto. 

>SELECT actor.name  
FROM actor JOIN casting ON actor.id = casting.actorid  
>>WHERE casting.movieid = (  
 -- 👇 id para pelicula Casablanca👇  
    SELECT movie.id  
    FROM movie  
    WHERE movie.title = 'Casablanca'  
);  


|name|
|--|
|Humphrey Bogart|
|Ingrid Bergman|
|Claude Rains|
|Peter Lorre|
|Paul Henreid|
|John Qualen|
|Curt Bois|
|Conrad Veidt|
|Madeleine LeBeau|



La version **sin** el **ON** sería así:

>SELECT actor.name  
>FROM actor JOIN casting  
 >          JOIN movie  
>> WHERE movie.title = 'Casablanca'  
       > AND actor.id = casting.actorid  
    > AND movie.id = casting.movieid;  





>SELECT actor.name    
>FROM actor     
> * JOIN casting ON actor.id = casting.actorid    
> * JOIN movie ON movie.id = casting.movieid     
>>WHERE movie.title = 'Casablanca' ;


|name|
|-------|
|Humphrey Bogart|
|Ingrid Bergman|
|Claude Rains|
|Peter Lorre|
|Paul Henreid|
|John Qualen|
|Curt Bois|
|Conrad Veidt|
|Madeleine LeBeau|



7.
Obtain the cast list for the film 'Alien'

>SELECT actor.name 
FROM movie JOIN casting ON casting.movieid =movie.id   
JOIN actor ON actor.id =casting.actorid 
>>WHERE movie.title= 'Alien';


>SELECT actor.name  
FROM movie, casting, actor
>>WHERE movie.title = 'Alien'
   AND movie.id= casting.movieid
   AND actor.id = casting.actorid;


name
Sigourney Weaver
Ian Holm
Harry Dean Stanton
Tom Skerritt
John Hurt
Veronica Cartwright
Yaphet Kotto


8.
List the films in which 'Harrison Ford' has appeared
SELECT movie.title
 FROM 
actor JOIN casting ON actor.id = casting.actorid 
         JOIN movie ON movie.id = casting.movieid 
WHERE actor.name = 'Harrison Ford'


title
Star Wars
Star Wars: Episode V - The Empire Strikes Back
Raiders of the Lost Ark
Star Wars: Episode VI - Return of the Jedi
Blade Runner
Indiana Jones and the Last Crusade
Fugitive, The
Apocalypse Now
Indiana Jones and the Temple of Doom
Air Force One
Witness
Clear and Present Danger
Patriot Games
American Graffiti
What Lies Beneath
Six Days Seven Nights
Working Girl
Sabrina
Devil's Own, The
Conversation, The
Regarding Henry
Frantic
Presumed Innocent
Random Hearts
Mosquito Coast, The


9.
List the films where 'Harrison Ford' has appeared - but not in the starring role. [Note: the ord field of casting gives the position of the actor. If ord=1 then this actor is in the starring role]
SELECT movie.title FROM movie JOIN casting ON movie.id = casting.movieid JOIN actor ON actor.id= casting.actorid WHERE actor.name = 'Harrison Ford' AND casting.ord <> 1;


title
Star Wars
Star Wars: Episode V - The Empire Strikes Back
Star Wars: Episode VI - Return of the Jedi
Apocalypse Now
American Graffiti
Conversation, The
.
https://zh.sqlzoo.net/wiki/More_JOIN_operations






CONSULTA MINIMA EN SQL

SELECT *
FROM  world;










name
continent
area
population
gdp
capital
tld
flag
Afghanistan
Asia
652230
25500100
20364000000
Kabul
.af
//upload.wikimedia.org/wikipedia/commons/9/9a/Flag_of_Afghanistan.svg
Albania
Europe
28748
2821977
12044000000
Tirana
.al
//upload.wikimedia.org/wikipedia/commons/3/36/Flag_of_Albania.svg
Algeria
Africa
2381741
38700000
207021000000
Algiers
.dz
//upload.wikimedia.org/wikipedia/commons/7/77/Flag_of_Algeria.svg
Andorra
Europe
468
76098
3222000000
Andorra la Vella
.ad
//upload.wikimedia.org/wikipedia/commons/1/19/Flag_of_Andorra.svg

y todos los demás países del mundo.
SELECT COUNT ( *)
FROM  people;





SELECT COUNT (*)
FROM  world;



195


Se pueden utilizar reductores en el SELECT sin el Group BY siempre que la tabla seleccionada sea a su vez una subtabla.


SELECT COUNT (*)
FROM people;

SELECT COUNT (user_id)
FROM people;

SELECT COUNT (*)
FROM people
WHERE age>30;
    EL orden de ejecucion es: from: people ten 300 personas, where tendrá 200, por ej, después al final se ehjecuta COUNT  por lo que tendrá ya el número calculado. 




0.1.2.4.5.6.7.8
