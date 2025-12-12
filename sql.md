##Домашнее задание «Работа с PostgreSQL. Создание БД»

## Схема базы данных 
<img width="663" height="754" alt="image" src="https://github.com/user-attachments/assets/2b7b5dd7-1f6f-4bf0-b3f9-6fc8d9ed8e2a" />
`

## Код SQL для создания базы данных

```sql
--жанр1
CREATE TABLE IF NOT EXISTS Genres (
id SERIAL PRIMARY KEY, 
name VARCHAR(80) NOT NULL
);
--исполнитель2
CREATE TABLE IF NOT EXISTS Performers (
id SERIAL PRIMARY KEY, 
name VARCHAR(60) NOT NULL 
);
--Исполнители-жанры3
CREATE TABLE IF NOT EXISTS Genre_Performer (
genre_id INTEGER REFERENCES Genres(id), 
performer_id INTEGER REFERENCES Performers(id),
CONSTRAINT pk PRIMARY KEY (genre_id, performer_id)
);

--Альбом4
CREATE TABLE IF NOT EXISTS Albums (
id SERIAL PRIMARY KEY, 
name VARCHAR(80) NOT NULL, 
YearOfRelease INTEGER NOT NULL
);
--ИСПОЛНИТЕЛЬ – АЛЬБОМ5
CREATE TABLE IF NOT EXISTS Album_Performer (
album_id INTEGER REFERENCES Albums(id), 
performer_id INTEGER REFERENCES Performers(id),
CONSTRAINT pk2 PRIMARY KEY (album_id, performer_id)
);

--Трек6
CREATE TABLE IF NOT EXISTS Tracks (
id SERIAL PRIMARY KEY, 
name VARCHAR(60) NOT NULL,duration INTEGER NOT NULL, 
album_id INTEGER NOT NULL REFERENCES Albums(id)
);

--Сборник7
CREATE TABLE IF NOT EXISTS Collections (
id SERIAL PRIMARY KEY, 
name VARCHAR(60) NOT NULL, 
YearOfRelease INTEGER NOT NULL 
);
--Сборник_треки8
CREATE TABLE IF NOT EXISTS Collection_Track (
collection_id INTEGER REFERENCES Collections(id), 
track_id INTEGER REFERENCES Tracks(id),
CONSTRAINT pk3 PRIMARY KEY (collection_id, track_id)
);
```