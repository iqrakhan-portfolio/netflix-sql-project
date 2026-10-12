# netflix-sql-project
A portfolio project analyzing Netflix movies and TV shows using SQL.
# 🎬 Netflix Movie & TV Show Analysis (SQL Project)

## 📌 Project Overview
This project provides an end-to-end analysis of Netflix content data using MySQL. The goal is to extract business insights regarding content distribution, top genres, country-wise content production, and duration patterns.

---

## 🛠️ Database Schema & Data Import

```sql
-- Step 1: Create Database
CREATE DATABASE IF NOT EXISTS netflix_db;
USE netflix_db;

-- Step 2: Create Table Schema
CREATE TABLE netflix_titles (
    show_id VARCHAR(10) PRIMARY KEY,
    type VARCHAR(15),
    title VARCHAR(150),
    director VARCHAR(150),
    country VARCHAR(100),
    release_year INT,
    rating VARCHAR(10),
    duration VARCHAR(20),
    genre VARCHAR(50)
);

-- Step 3: Insert Sample Data
INSERT INTO netflix_titles VALUES
('s1', 'Movie', '3 Idiots', 'Rajkumar Hirani', 'India', 2009, 'PG-13', '170 min', 'Comedies'),
('s2', 'TV Show', 'Stranger Things', 'The Duffer Brothers', 'United States', 2016, 'TV-14', '4 Seasons', 'Sci-Fi'),
('s3', 'Movie', 'RRR', 'S.S. Rajamouli', 'India', 2022, 'TV-MA', '182 min', 'Action'),
('s4', 'TV Show', 'Money Heist', 'Álex Pina', 'Spain', 2017, 'TV-MA', '5 Seasons', 'Crime'),
('s5', 'Movie', 'Inception', 'Christopher Nolan', 'United States', 2010, 'PG-13', '148 min', 'Sci-Fi'),
('s6', 'Movie', 'Dangal', 'Nitesh Tiwari', 'India', 2016, 'PG', '161 min', 'Drama'),
('s7', 'TV Show', 'Sacred Games', 'Anurag Kashyap', 'India', 2018, 'TV-MA', '2 Seasons', 'Crime'),
('s8', 'Movie', 'The Dark Knight', 'Christopher Nolan', 'United States', 2008, 'PG-13', '152 min', 'Action'),
('s9', 'TV Show', 'Squid Game', 'Hwang Dong-hyuk', 'South Korea', 2021, 'TV-MA', '1 Season', 'Drama'),
('s10', 'Movie', 'Lagaan', 'Ashutosh Gowariker', 'India', 2001, 'PG', '224 min', 'Drama'),
('s11', 'Movie', 'The Irishman', 'Martin Scorsese', 'United States', 2019, 'R', '209 min', 'Dramas'),
('s12', 'TV Show', 'Breaking Bad', 'Vince Gilligan', 'United States', 2008, 'TV-MA', '5 Seasons', 'Crime'),
('s13', 'Movie', 'Spirited Away', 'Hayao Miyazaki', 'Japan', 2001, 'PG', '125 min', 'Anime'),
('s14', 'TV Show', 'The Crown', 'Peter Morgan', 'United Kingdom', 2016, 'TV-MA', '6 Seasons', 'Dramas'),
('s15', 'Movie', 'PK', 'Rajkumar Hirani', 'India', 2014, 'PG-13', '153 min', 'Comedies'),
('s16', 'TV Show', 'Dark', 'Baran bo Odar', 'Germany', 2017, 'TV-MA', '3 Seasons', 'Sci-Fi'),
('s17', 'Movie', 'Extraction', 'Sam Hargrave', 'United States', 2020, 'R', '116 min', 'Action'),
('s18', 'TV Show', 'The Witcher', 'Lauren Schmidt Hissrich', 'United States', 2019, 'TV-MA', '3 Seasons', 'Action'),
('s19', 'Movie', 'Zindagi Na Milegi Dobara', 'Zoya Akhtar', 'India', 2011, 'PG-13', '155 min', 'Comedies'),
('s20', 'TV Show', 'Attack on Titan', 'Tetsuro Araki', 'Japan', 2013, 'TV-MA', '4 Seasons', 'Anime');

---

## 📊 Business Analysis & SQL Queries

### 1. Count the number of Movies vs TV Shows
```sql
SELECT type, COUNT(*) AS total_count
FROM netflix_titles
GROUP BY type;

### 2. Find all Movies released in the year 2021
```sql
SELECT title, release_year, director, genre
FROM netflix_titles
WHERE type = 'Movie' AND release_year = 2021;

### 3. Find the top 3 most common genres on Netflix
```sql
SELECT genre, COUNT(*) AS total_shows
FROM netflix_titles
GROUP BY genre
ORDER BY total_shows DESC
LIMIT 3;

### 4. List all content produced in 'India'
```sql
SELECT title, type, release_year, director
FROM netflix_titles
WHERE country = 'India';

### 5. Find movies with duration greater than 150 minutes
```sql
SELECT title, duration, release_year
FROM netflix_titles
WHERE type = 'Movie' 
AND CAST(SUBSTRING_INDEX(duration, ' ', 1) AS UNSIGNED) > 150;
```

---

## 🚀 Key Takeaways & Insights
* **Content Breakdown:** Netflix offers a balanced mix of feature films and binge-worthy multi-season TV shows.
* **Top Regional Hubs:** India and the United States are among the top primary content contributors in the dataset.
* **Popular Genres:** Action, Drama, and Comedies dominate the catalog content.

