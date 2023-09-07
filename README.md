# Enroute React Node.js Challenge
 Front-End, Back-End and Database with Docker
 
## How to install and run the project

### Prerequisites
Installed programs:
* Git (I used version 2.36.0)
* Docker (I used version 24.0.5)

Other:
* At least 5 GB of free space in the disk where you have Docker installed
* `http://localhost:3000`, `http://localhost:3001` and `localhost:5432` available on your computer to be used

### How to run the applications (for Windows)
1. Clone this repository in your local computer with the command: `git clone https://github.com/CesarEGomezG/enroute-cesar.git`
2. Go into this folder with: `cd enroute-cesar`
3. Clone the front-end repository inside /enroute-cesar directory: `git clone https://github.com/CesarEGomezG/enroute-frontend.git`
4. Clone the back-end repository inside /enroute-cesar directory: `git clone https://github.com/CesarEGomezG/enroute-backend.git`
5. Run Docker Compose to build and run the front-end, back-end, and database images: `docker-compose up -d`
6. Get into the terminal of the database container with: `docker-compose exec postgres bash`
7. Authenticate in PostgreSQL with: `psql --username {POSTGRES_USER} --db {POSTGRES_DB} --password` where `{POSTGRES_USER}` and `{POSTGRES_DB}` have to be replaced by the values of the environment variables located in the 'postgres' service of the docker-compose.yml file
8. Type the user password: `{POSTGRES_PASSWORD}` retrieved from the docker-compose.yml file
9. Create the 'Color' table with the query:
```
create table "Color" (
 id smallint primary key,
 name varchar(16) unique not null,
 multiplier numeric(17, 5) unique not null,
 tolerance numeric(6, 3) unique
);
```
10. Insert data to the new table with the query:
```
insert into "Color" (id, name, multiplier, tolerance) values
(0, 'pink', 0.001, null),
(1, 'silver', 0.01, 10),
(2, 'gold', 0.1, 5),
(3, 'black', 1, null),
(4, 'brown', 10, 1),
(5, 'red', 100, 2),
(6, 'orange', 1000, 0.05),
(7, 'yellow', 10000, 0.02),
(8, 'green', 100000, 0.5),
(9, 'blue', 1000000, 0.25),
(10, 'violet', 10000000, 0.1),
(11, 'gray', 100000000, 0.01),
(12, 'white', 1000000000, null);
```
11. Exit PostgreSQL with: `exit`
12. Exit the database container terminal with: `exit`

Finally, you can go to `http://localhost:3000` in your local computer browser and you will see the front-end application running there. It will have connection with the API running in `http://localhost:3001` and the API will have connection with the database running on `localhost:5432`

### How to stop and remove the applications
1. Stop the three Docker containers with: `docker-compose down`
2. Check the ids of the three Docker images (enroute-cesar-frontend, enroute-cesar-backend, and enroute-cesar-postgres) with: `docker images`
3. Remove those images to free disk space with: `docker rmi {idOfFrontend} {idOfBackend} {idOfPostgres}` where `{idOf____}` are the ids of the three docker images obtained in the previous step

## How it looks
![calculator](https://github.com/CesarEGomezG/enroute-cesar/assets/76894869/727f5d6c-0ebb-46ca-aba0-905ccee8624d)
