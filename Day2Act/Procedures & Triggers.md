`                  `STORED PROCEDURES & TRIGGERS

1.Display the name of movies, movie type is starts with Drama.

`     `CREATE PROCEDURE `getMovieName` ()

`    `BEGIN

`    `select moviename from movie where mtype like "drama%"; 

`    `END

`   `call demo.getMovieName();

`   `OUTPUT:

`   `'bahubali'



2.Display the count of movies, having length       above 18.

CREATE PROCEDURE `getCount` ()

BEGIN

select count(moviename) from movie where length>18";

END

call demo.getCount();

OUTPUT:

2

`  `3.Display the movie having minimum length.

`         `CREATE PROCEDURE `getMin` () 

`          `BEGIN

`          `select moviename from movie where length=(select min(length) from movie);

`          `END

`          `call demo.getMin();



`      `OUTPUT:

`        `‘aval’

\4. Display all the details of movie, the language thatfirst name starts with ‘T’

`          `CREATE PROCEDURE `getDetails` () 

`          `BEGIN

`          `select moviename from movie where language like “t%”;

`          `END

`          `call demo.getDetails();



`      `OUTPUT:

`        `‘bahubali’ 

`        `‘2.0’

`        `‘aval’ 

\5. Display the movie name, hero name, heroine name whose having maximum length.

CREATE PROCEDURE `getRes` ()

BEGIN

select moviename, heroname, heroinename from movie where length=(Select     max(length) from movie);

END

call demo.getRes();

OUTPUT:

‘bahubali’

‘prabhas’

‘tamannah’

`                                                                       `Triggers

**1.Inserting values into table by using trigger.**

create table sample(sid int(50),itemid int(3),price int(8),total int(14));

insert into sample values (1,2,3,4);

select \* from sample;

Here values as (1,2,3,4) will be present in sid, itemid, price, total


create trigger t1 before insert on sample

`    `-> for each row

`    `-> set new.total=new.price+new.itemid;

insert into sample values(5,19,10,0);

select \* from sample;

so now the output will be updated i.e. sid, itemid, price, total will have another updated values as (5,19,10,29)


