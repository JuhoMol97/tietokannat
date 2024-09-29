MODULE 3:

teht 1:
select * from goal;
![ruudunkaappaus](module3_teht1.png)

teht 2:
select name, type from airport where iso_country = "FI";
![ruudunkaappaus](module3_teht2.png)

teht 3:
select name from airport where iso_country = "FI" order by name;
![ruudunkaappaus](module3_teht3.png)

teht 4:
select name, type from airport where iso_country = "FI" order by type, name;
![ruudunkaappaus](module3_teht4.png)

teht 5:
select name from country where name like "F%";
![ruudunkaappaus](module3_teht5.png)

teht 6:
select name from country where name like "%F%";
![ruudunkaappaus](module3_teht6.png)

teht 7:
select location from game where screen_name = "Vesa";
![ruudunkaappaus](module3_teht7.png)

teht 8:
select co2_consumed from game where screen_name = "Ilkka";
![ruudunkaappaus](module3_teht8.png)

teht 9:
select distinct co2_budget from game;
![ruudunkaappaus](module3_teht9.png)




MODULE 4:

teht 1:
select country.name as "country name", airport.name as "airport name" from country, airport where airport.iso_country = country.iso_country and country.name = "Iceland";
![ruudunkaappaus](module4_teht1.png)

teht 2:
select airport.name as "airport name" from airport, country where airport.iso_country = country.iso_country and country.name = "France" and airport.type = "large_airport";
![ruudunkaappaus](module4_teht2.png)

teht 3:
select country.name as "country_name", airport.name as "airport_name" from airport, country where airport.iso_country = country.iso_country and country.continent = "AN";
![ruudunkaappaus](module4_teht3.png)

teht 4:
select airport.elevation_ft from airport, game where game.location = airport.ident and game.screen_name = "Heini";
![ruudunkaappaus](module4_teht4.png)

teht 5:
select airport.elevation_ft * 0.3048 as elevation_m from airport, game where game.location = airport.ident and game.screen_name = "Heini";
![ruudunkaappaus](module4_teht5.png)

teht 6:
select airport.name from airport, game where game.location = airport.ident and game.screen_name = "Ilkka";
![ruudunkaappaus](module4_teht6.png)

teht 7:
select country.name from airport, game, country where game.location = airport.ident and airport.iso_country = country.iso_country and game.screen_name = "Ilkka";
![ruudunkaappaus](module4_teht7.png)

teht 8:
select distinct goal.name from goal_reached, goal, game where game.screen_name = "Heini" and goal_reached.game_id = game.id and goal_reached.goal_id = goal.id;
![ruudunkaappaus](module4_teht8.png)

teht 9:
select airport.name from airport, game, goal_reached, goal where game.screen_name = "Ilkka" and goal.name = "clouds" and airport.ident = game.location and game.id = goal_reached.game_id and goal_reached.goal_id = goal.id;
![ruudunkaappaus](module4_teht9.png)

teht 10:
select country.name from airport, game, goal_reached, goal, country where game.screen_name = "Ilkka" and goal.name = "clouds" and airport.ident = game.location and game.id = goal_reached.game_id and goal_reached.goal_id = goal.id and airport.iso_country = country.iso_country;
![ruudunkaappaus](module4_teht10.png)




MODULE 5:

teht 1:
select country.name as "country name", airport.name as "airport name" from airport inner join country on airport.iso_country = country.iso_country and country.name = "Finland" where airport.scheduled_service = "yes";
![ruudunkaappaus](module5_teht1.png)

teht 2:
select screen_name, airport.name from airport inner join game on game.location = airport.ident;
![ruudunkaappaus](module5_teht2.png)

teht 3:
select screen_name, country.name from game inner join airport on game.location = airport.ident inner join country on country.iso_country = airport.iso_country;
![ruudunkaappaus](module5_teht3.png)

teht 4:
select airport.name, screen_name from airport left join game on game.location = airport.ident where airport.name like "%hels%";
![ruudunkaappaus](module5_teht4.png)

teht 5:
select goal.name, screen_name from game right join goal_reached on game.id = goal_reached.game_id right join goal on goal.id = goal_reached.goal_id;
![ruudunkaappaus](module5_teht5.png)




MODULE 6:

teht 1:
select name from country where iso_country in(select iso_country from airport where name like "Satsuma%");
![ruudunkaappaus](module6_teht1.png)

teht 2:
select name from airport where iso_country in(select iso_country from country where name = "Monaco");
![ruudunkaappaus](module6_teht2.png)

teht 3:
select screen_name from game where id in(select game_id from goal_reached where goal_id in(select id from goal where name = "CLOUDS"));
![ruudunkaappaus](module6_teht3.png)

teht 4:
select name from country where iso_country not in(select iso_country from airport);
![ruudunkaappaus](module6_teht4.png)

teht 5:
select name from goal where id not in(select goal_id from goal_reached where game_id in(select id from game where screen_name = "Heini"));
![ruudunkaappaus](module6_teht5.png)




MODULE 7:

teht 1:
select max(elevation_ft) from airport;
![ruudunkaappaus](module7_teht1.png)

teht 2:
select continent, count(*) from country group by continent;
![ruudunkaappaus](module7_teht2.png)

teht 3:
select screen_name, count(*) from game inner join goal_reached on game.id = goal_reached.game_id inner join goal on goal.id = goal_reached.goal_id group by screen_name;
![ruudunkaappaus](module7_teht3.png)

teht 4:
select screen_name from game where co2_consumed in(select min(co2_consumed) from game);
![ruudunkaappaus](module7_teht4.png)

teht 5:
select country.name, count(*) from country inner join airport on country.iso_country = airport.iso_country group by country.name order by count(*) desc limit 50;
![ruudunkaappaus](module7_teht5.png)

teht 6:
select country.name from country inner join airport on country.iso_country = airport.iso_country group by country.name having count(*) >= 1000;
![ruudunkaappaus](module7_teht6.png)

teht 7:
select name from airport where elevation_ft in(select max(elevation_ft) from airport);
![ruudunkaappaus](module7_teht7.png)

teht 8:
select country.name from country inner join airport on airport.iso_country = country.iso_country where elevation_ft in(select max(elevation_ft) from airport);
![ruudunkaappaus](module7_teht8.png)

teht 9:
select count(*) from game inner join goal_reached on game.id = goal_reached.game_id inner join goal on goal.id = goal_reached.goal_id where screen_name = "Vesa" group by goal.id;
![ruudunkaappaus](module7_teht9.png)

teht 10:
select name from airport where latitude_deg in(select min(latitude_deg) from airport);
![ruudunkaappaus](module7_teht10.png)




MODULE 8:

teht 1:
update game set game.location = (select ident from airport where name = "Nottingham Airport"), game.co2_consumed = (select co2_consumed + 500 from game where screen_name = "Vesa") where screen_name = "Vesa"; 
![ruudunkaappaus](module8_teht1.png)

teht 2:
a. goal_reached

teht 3:
delete from goal_reached;

teht 4:
delete from game;
