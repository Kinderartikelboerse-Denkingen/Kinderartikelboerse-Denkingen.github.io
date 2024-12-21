---
title: Database
layout: default
parent: Backend
---

We use a Postgres database running in a Docker container.

## Getting started

After starting the database with `docker-compose up` you can access the database with any Postgres client.

Postgres is running on `localhost:5432` with the user `postgres` and the password `postgres` and the database `postgres`.

If you plan on making this a public service, you should change the password in the `docker-compose.yml` file.

## Database schema

This is the naive idea of the database schema. This is not final and will most likely change in the future.

```mermaid
erDiagram
    Event {
        int id
        Date date
    }
    Registration {
        int id
        Event event
        Seller user
    }
    Seller {
        int id
        string email
        string password
        string firstName
        string lastName
        string address
        string phoneMobile
        string phoneLandline
    }
    Lock {
        int id
        Seller seller
        string reason
    }
    Item {
        int id
        Registration registration
        string description
        string size
        int price
    }
    
    Registration }o--|| Event : ""
    Registration }o--|| Seller : ""
    Registration ||--o{ Item : ""
    Seller }o--|| Lock : ""
```


----

