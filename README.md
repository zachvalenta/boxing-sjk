# overview

Flask app for a database of the fights I've watched.

# todo

- [ ] SQLite - seed
- [ ] Postgres - dump and load

# notes

* how rounds are judged: clean punching, effective aggression, ring generalship, defense

prelim data model
```sql
create table boxer (
    boxer_id serial primary key,
    gname varchar(80),
    sname varchar(80),
    nationality varchar(80),
    active_start date,
    active_end date
);

create table fight (
    fight_id serial primary key,
    broadcast date,
    watched date,    
    venue varchar(80),
    network varchar(80),
    scoring jsonb, -- could be in separate table but how to deal w/ variable fight length? all sports would have this problem though
    comments jsonb
);

create table boxer_fight (
    boxer_fight_id serial primary key,
    fight_id, -- constraint
    boxer_a,
    boxer_b
);

create table division (
    division_id serial primary key,
    name varchar(80),  -- is name reserved word? is text?
    weight_limit integer
);

create table boxer_division (
    boxer_division_id serial primary key,
    boxer_id,  -- constraint
    division_id 
);
```
