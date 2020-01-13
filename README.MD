## DB Commands

### Exporting Data Heroku

- heroku pg:backups:capture
- heroku pg:backups:download

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