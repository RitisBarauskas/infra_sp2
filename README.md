# YaMDb API
OpenAPI specification: [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc).

API queries start with `/api/v1/`

## Description 
The YaMDb project collects user reviews of works.
The works are divided into categories: Books, Movies, Music.

## User registration algorithm

1. User sends a request with the `email` parameter to `/auth/email/`.
2. YaMDB sends an email with a `confirmation_code` to the `email` address.
3. User sends request with `email` and `confirmation_code` to `/auth/token/`, user receives a `token` (JWT token) in response.
4. If desired, the user sends a `PATCH` request to `/users/me/` and completes the fields in their profile (see documentation for description of fields).

## User roles

* **Anonymous** - can browse descriptions, read reviews and comments.
* **Authenticated User** - may, like Anonymous, read anything, in addition may post reviews and rate works (movies/books/songs), may comment on others' reviews and rate them; may edit and delete their own reviews and comments.
* **Moderator** - the same rights as an Authenticated User plus the right to remove any reviews and comments.
* **Administrator** - full rights to manage the project and all its contents. Can create and delete categories and works. Can assign roles to users.
* **Django Administrator** - The same rights as the Administrator role.

## Install

#### 1. Install docker and docker-compose

Если у вас уже установлены docker и docker-compose, этот шаг можно пропустить, иначе можно воспользоваться официальной [инструкцией](https://docs.docker.com/engine/install/).

#### 2. Run Docker container
```bash
docker-compose up
```
### 3. Stop Docker container
```bash
docker-compose down
```

## Use
### 1. Create migrations
```bash
docker-compose run web python manage.py makemigrations
```

### 2. Migrate
```bash
docker-compose run web python manage.py migrate
```

### 3. Create Superuser Django
```bash
docker-compose run web python manage.py createsuperuser
```

### 4. Initial start-data:
```bash
docker-compose run web python manage.py loaddata fixtures.json
```

## Author
Ritis Barauskas, fullstack developer
+79526578502 (tel, WA, TG)