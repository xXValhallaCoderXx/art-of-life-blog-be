# Setup Admin User

- Ensure you have Heroku CLI
- `heroku login`

## DB Commands

### Exporting Data Heroku

- heroku pg:backups:capture -a art-of-life-blog-be
- heroku pg:backups:download -a art-of-life-blog-be

### Enter Docker DB

- docker exec -it art_of_life bash
- psql -U xxvalinorxx -d art_of_life

## Copy Data Into Docker DB

- docker cp latest.dump art_of_life:/var/lib/postgresql/data
- docker exec art_of_life pg_restore -U xxvalinorxx -d art_of_life /var/lib/postgresql/data/latest.dump -c

## Copy Data FROM Local Docker DB

- docker exec art_of_life pg_dump -U xxvalinorxx art_of_life > backup.sql

### PSQL Commands

- \d view schema

# Initial Setup

- Run `docker-compose up --build`
- With the `latest.dump` insert it in the DB
- Run `docker cp latest.dump art_of_life:/var/lib/postgresql/data` to copy the dump into the docker
- Run `docker exec art_of_life pg_restore -U xxvalinorxx -d art_of_life /var/lib/postgresql/data/latest.dump -c`
- To check the data is in DB run `docker exec -it art_of_life bash` then `psql -U xxvalinorxx -d art_of_life`
- View current schema `\d`

### Heroku commands

- `heroku config -a art-of-life-blog-be` : Enviroment Variables
