1.Display the name of movies, movie type is starts with Drama.

SELECT Moviename from Movie where Movietype like '%Drama';

2.Display the movies acted by actor Ayushmann.

select Moviename from Movie where Heroname like 'Ayushmann';

3.Display the count of movies, having length above 18.

Select count(Moviename) from Movie where Length>18;

\4. Display the movie having minimum length.

select Moviename from Movie where Length=(select min(Length) from Movie);

5.Display all the details of movie, the language that first name starts with ‘T’

select \* from Movie where Language like 'T%';

6.Display the movie name, hero name, heroine name whose having maximum length.

select Moviename,Heroname,Heroinename from Movie where Length=(select max(Length) from Movie);

7.Display the movie name, hero name, heroine name the movie released after 15 march 2018.

select Moviename,Heroname,Heroinename from Movie where Releaseddate > '2018-03-15';

8.Display the count of thriller movies.

`  `select count(Moviename) from Movie where Movietype like '%Thriller%';

9.Display the count of movies whose released before 15 march 2018.

select count(Moviename) from Movie where Releaseddate < '2018-03-15';

10.Display the release date of the movie name ‘Zero’.

select Releaseddate from Movie where Moviename = "Zero"

11.Display the actor name that acted with ‘Amy’.

select Heroname from Movie where Heroinename ="Amy";

12.Display the Count of maximum movies released in a month of October.

select count(Moviename)from Movie where Releaseddate like '%-10-%';

13.Display the movienames whose production id for different languages.

select distinct Productionid,Moviename from Movie;


Advanced Query by using the Two Tables:

\1.

Write the query to display productionid, production name with total number movies produced by each.

SELECT Productions.productionid,Productions.productionname,COUNT(\*) FROM Productions INNER JOIN Movie ON movie.productionid=Productions.productionid group by Productionname;

\2.

Write the query to display production name, owner name have produced more than 2 movies.

SELECT productions.productionname,productions.ownername,COUNT(\*) FROM productions INNER JOIN movie ON movie.productionid = productions.productionid group by productionname HAVING COUNT(\*)>2;

\3.

Write the query to display production name, owner name have produced maximum movies

SELECT productions.productionname,productions.ownername FROM productions INNER JOIN movie ON movie.productionid = productions.productionid group by productionname ORDER BY COUNT(\*) DESC LIMIT 1;


\4.

Write the query to display the moviename, heroname and productionname acted in the producer name= ’Subaskaran’.

SELECT movie.moviename,movie.HeroName,productions.productionname

FROM productions INNER JOIN movie ON movie.productionid = productions.productionid WHERE ownername='Subaskaran';

\5. 

Write the query to display the moviename, heroname whose productionid ends with 82.

SELECT movie.moviename,movie.HeroName FROM productions INNER JOIN movie ON movie.productionid = productions.productionid WHERE movie.productionid LIKE '%82';

\6.

Write the query to display the productionname, ownername who has not produced the movie.

SELECT productions.productionname,productions.ownername FROM productions LEFT JOIN movie ON movie.productionid = productions.productionid WHERE moviename IS NULL;

\7. 

Write the query to display the productionname, ownername who has not produced the ‘hindi’ movie.

SELECT p.Productionname,p.Ownername from productions p left join movie m on m.Productionid=p.productionid and m.language="Hindi" where m.Language is null;

\8.

Write the query name to display the heroinename who acted in the different productions but not in same production id.

INSERT INTO basic SELECT movie.Heroine FROM movie INNER JOIN productions ON productions.productionid=movie.productionid GROUP BY(ownername);

SELECT heroine from basic GROUP BY heroine HAVING COUNT(heroine)>1;

\9.

Write the query to display the heroname who acted in maximum languages.

SELECT distinct Heroname ,Language , count(Heroname) as result from  movie group by(Language) order by (result) desc limit 1   ;

\10.

Write the query to display the production name, owner name who has produced movie for more languages.

SELECT distinct p.Productionname,p.Ownername ,count(p.Productionname) as counter  from  movie as m right join productions as p ON  m.productionid =p.productionid  group by(m.language) order by(counter) desc limit 1;

\11.

Write the query to display the productionname, producername who has not produced any movie.

SELECT p.Ownername ,p.Productionname from  movie as m right join productions as p ON  m.productionid =p.productionid where m.moviename is  null ;






