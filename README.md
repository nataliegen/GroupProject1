# GroupProject1

## Team Information
21482 Group 3 

### Team Members 
1. Natalie Gen
2. Priyanka Govani
3. Truett Thompson
4. Patrick Schutz
5. Anika Kaushik

## Data Model

Our data model represents the structure of a music web player, facilitating user interaction with songs, artists, playlists, and playback tracking.
The Users entity serves as the foundation, storing details such as username, email, name, date of birth, and country. Each user can create multiple Playlists, which contain songs and are associated with attributes like privacy settings, creation date, and like count.
The MusicLibrary table tracks which songs a user has added to their library, along with metadata such as play count, skip count, and last played date. This table enables personalized listening experiences.
To track user activity, the PlayerSessions table logs each listening session, linking a user and a song to timestamps that mark when a session starts and ends. This provides insights into user listening behavior.
The Songs table stores metadata about each song, including its title, duration, release date, and links to the Artist and Album it belongs to. Each song is categorized by genres through the SongGenres table, which assigns genres to songs with relevance scores.
The Artist table maintains information about artists, including their name, country, label, and biography. Artists may release multiple albums, and the Album table captures this relationship by linking albums to artists. The album also records data such as total tracks, duration, album type, and the primary genre.
The Genres table defines different musical genres, with attributes such as description, country of origin, and historical era. Artists can be associated with multiple genres through the ArtistGenres table, which includes a popularity score for each genre assigned to an artist.
Lastly, the PlaylistSongs table functions as an associative entity linking playlists to songs. It tracks when a song was added, the last played date, play count, and times skipped, allowing users to analyze their playlist interactions.
This data model enables a fully functional music web player, allowing users to manage their libraries, play songs, create and share playlists, and explore music across genres, artists, and albums.

<img width="845" alt="Screenshot 2025-03-18 at 10 59 13 PM" src="https://github.com/user-attachments/assets/daca5666-85a3-49af-bbfc-2b0f1b1a7d9f" />


**Users** – Stores user details
Attributes:
- Primary Key: userID
- username
- email
- last_Name
- first_Name
- country
- date_of_birth

**Relationships**:
- One-to-Many with PlayerSessions (each user can have multiple sessions).
- One-to-Many with Playlists (each user can create multiple playlists).
- One-to-Many with MusicLibrary.

**MusicLibrary** – Represents a user's music collection
Attributes:
- Primary Key: libraryID
- Foreign Key: userID
- Foreign Key: songID
- play_count
- skip_count
- date_added
- last_played

**Relationships**:
- Many-to-One with Users (each user can have a music library).
- Many-to-One with Songs (each library entry references a song).

**Songs** – Contains song data
Attributes:
- Primary Key: songID
- Foreign Key: artistID
- Foreign Key: albumID
- title
- duration
- release_date

**Relationships**:
- Many-to-One with Artist (each song has one artist).
- Many-to-One with Album (each song belongs to one album).
- Many-to-Many with Genres via SongGenres (each song can belong to multiple genres).
- Many-to-Many with Playlists via PlaylistSongs (a song can be in multiple playlists).
- One-to-Many with MusicLibrary (a song can be played multiple times).

**Artist** – Contains information about each artist
Attributes:
- Primary Key: artistID
- name
- country
- label
- bio

**Relationships**:
- One-to-Many with Songs (an artist can have many songs).
- Many-to-Many with Genres via ArtistGenres (an artist can be associated with multiple genres).
- One-to-Many with Album (an artist can have multiple albums).

**Album** – Stores information about albums
Attributes:
- Primary Key: albumID
- Foreign Key: artistID
- Foreign Key: primary_genreID
- title
- release_date
- record_label
- total_tracks
- duration
- album_type

**Relationships**:
- One-to-Many with Songs (each album contains multiple songs).
- Many-to-One with Artist (each album has one artist).
- Many-to-One with Genres (each album has one genre).

**PlayerSessions** – Tracks user listening sessions
Attributes:
- Primary Key: sessionID
- Foreign Key: userID
- Foreign Key: songID
- start_time
- end_time

**Relationships**:
- Many-to-One with Users (each session belongs to one user).
- Many-to-One with Songs (each session records a song being played).

**Playlists** – Represents user-created playlists
Attributes:
- Primary Key: playlistID
- Foreign Key: userID
- name
- privacy_type
- creation_date
- like_count

**Relationships**:
- Many-to-One with Users (each playlist is created by one user).
- Many-to-Many with Songs via PlaylistSongs (a playlist can contain multiple songs).

**PlaylistSongs** – Associative entity between Playlists and Songs
Attributes:
- Foreign Key: songID
- Foreign Key: playlistID
- added_date
- playlist_play_count
- playlist_last_played
- times_skipped

**Relationships**:
- Many-to-One with Songs (each playlist entry references a song).
- Many-to-One with Playlists (each entry belongs to a playlist).

**Genres** – Stores music genres
Attributes:
- Primary Key: genreID
- name
- description
- origin_country
- era

**Relationships**:
- Many-to-Many with Songs via SongGenres (a song can belong to multiple genres).
- Many-to-Many with Artists via ArtistGenres (an artist can be associated with multiple genres).
- One-to-May with Album (an album can be associated with multiple genres).

**SongGenres** – Associative entity between Songs and Genres
Attributes:
- Foreign Key: songID
- Foreign Key: genreID
- genre_relevance
- date_assigned

**Relationships**:
- Many-to-One with Songs (each entry references a song).
- Many-to-One with Genres (each entry references a genre).

**ArtistGenres** – Associative entity between Artists and Genres
Attributes:
- Foreign Key: artistID
- Foreign Key: genreID
- dominant_genre
- popularity_score

**Relationships**:
- Many-to-One with Artists (each entry references an artist).
- Many-to-One with Genres (each entry references a genre).

## Data Dictionary 
![Screenshot 2025-03-18 233344](https://github.com/user-attachments/assets/dddf3603-9596-4a29-b978-104911f12306)
![Screenshot 2025-03-18 233355](https://github.com/user-attachments/assets/f674d3db-d72d-41e8-8f2f-6215e39578a1)
![Screenshot 2025-03-18 233407](https://github.com/user-attachments/assets/c0166899-267c-4043-a7c6-98eee918ece6)
![Screenshot 2025-03-18 233417](https://github.com/user-attachments/assets/4af48ed1-15f9-4469-a08a-7581ea05a3dc)
![Screenshot 2025-03-18 233424](https://github.com/user-attachments/assets/82f3c691-4c80-4fab-a394-e7a46febe67d)


## Queries 
TP_Q1 : Write a query which displays the playlistName and like count that has the most like counts for each user. 

Description: This query identifies the most liked playlist for each user by retrieving the playlist with the highest number of likes. It helps the platform understand which types of playlists users engage with the most, allowing for better playlist recommendations and personalized curation. Knowing a user’s most liked playlist can drive engagement strategies, such as suggesting similar playlists, promoting user-created content, or featuring popular playlists. 

<img width="541" alt="Screenshot 2025-03-18 at 11 08 50 PM" src="https://github.com/user-attachments/assets/a7ed1c58-139c-4a9d-8797-d77889d4e120" />


TP_Q2 : Write a query which displays the first, last name, and date of birth for every user who was born after 1990. Order it by date of birth going from earliest to latest. 

Description: This query retrieves the first name, last name, and date of birth for all users born after 1990, ordering them by date of birth from earliest to latest. This information is useful for understanding the age demographics of the platform’s user base, allowing for age-targeted recommendations, marketing campaigns, and content curation. By analyzing user age groups, the platform can tailor playlists, promotions, and advertisements to specific generational preferences. 

<img width="443" alt="Screenshot 2025-03-18 at 11 09 18 PM" src="https://github.com/user-attachments/assets/5172d00b-f168-44a1-85a9-d922c207f40e" />


TP_Q3 : Write a query that shows artists whose songs have the highest play count by users in the US. 

Description: This query retrieves the artist whose songs have the highest total play count by users located in the United States. By filtering based on user location and aggregating total plays per artist, this query helps identify the most popular artists among US listeners. This insight is valuable for targeted marketing campaigns, regional promotions, and exclusive content strategies. Streaming services can use this data to curate country-specific playlists, recommend trending US-based artists, or negotiate regional sponsorship deals.

<img width="409" alt="Screenshot 2025-03-18 at 11 09 38 PM" src="https://github.com/user-attachments/assets/af81129b-083b-45b1-a807-1d322cc270b8" />


TP_Q4 : Write a query that displays songs and the artist of the songs which are 50% country

Description: This query retrieves songs and their artists where at least 50% of the song’s genre classification is country. Many songs fall into multiple genres, so this query helps identify tracks that are significantly influenced by country music but may also belong to other genres. Understanding partially country songs allows the platform to enhance personalized recommendations, helping users discover songs that blend country with other styles. 

<img width="522" alt="Screenshot 2025-03-18 at 11 11 53 PM" src="https://github.com/user-attachments/assets/f606e8c5-519d-4674-aba7-0e8ae7441676" />


TP_Q5: Write a query to list song name and artist of the song that has been skipped the most time in each playlist.

Description: This query helps identify the most skipped song in each playlist, showing the song name and its artist. It does this by comparing the skip count of each song to the highest skip count in that playlist. By analyzing this data, the platform can pinpoint which songs are most likely interrupting the listening experience. This insight can be used to improve playlist recommendations and make the overall listening experience better for users.

<img width="521" alt="Screenshot 2025-03-18 at 11 13 29 PM" src="https://github.com/user-attachments/assets/20d12a6f-6bce-405b-838f-c4c537ae80a9" />


TP_Q6 : Write a query which displays the top 5 most played songs for a given user (2). List the song title, artist, album, genre and play count. 

Description: This query retrieves the top 5 most played songs for user 2, listing the song title, artist, album, genre, and play count. Understanding a user’s most frequently played songs helps the platform enhance personalized recommendations, curate better auto-generated playlists, and improve music discovery. Which can also be used to suggest similar songs or artists, increasing user engagement and retention. It allows the platform to identify music trends among users, which can be leveraged for targeted promotions, concert recommendations, or exclusive content offerings.

![image](https://github.com/user-attachments/assets/fbebd280-04cb-4f4f-913c-43d28cb7fd95)


TP_Q7 : Write a query that retrieves the total number of play sessions per country, calculates the average session duration in seconds for each country, and counts the total number of songs users from each country have in their music library

Description: This query provides insights into user engagement by analyzing music consumption patterns across different countries. It identifies which countries have the highest number of play sessions, the average session duration per country, and the total number of songs users from each country have in their libraries.  It can also be used to enhance user retention by offering personalized playlists, country-specific promotions, or localized content based on session activity and song preferences.

<img width="504" alt="Screenshot 2025-03-18 at 11 13 01 PM" src="https://github.com/user-attachments/assets/357d4490-8eba-496f-85a3-61451f379ff0" />


TP_Q8 : Write a query that counts all the users that have a play session for 10 mins or more

Description: This query identifies users who have listened for 30 mins or longer sessions, highlighting highly engaged listeners who frequently return to the platform. Understanding which users exceed this threshold helps improve user retention strategies, such as personalized recommendations, exclusive promotions, or loyalty rewards. For free-tier users, this data can drive targeted ads or subscription offers, while premium users may receive early access to new features or curated content.

<img width="554" alt="Screenshot 2025-03-18 at 11 10 37 PM" src="https://github.com/user-attachments/assets/51f7e814-3443-457a-af36-30787c7f3a4b" />


TP_Q9 : Write a query to list the average play count of songs by genre

Description: This query calculates the average play count of songs grouped by genre, providing insights into which genres receive the most and least engagement on the platform. By analyzing the average number of plays per genre, the platform can identify trends in user preferences, helping refine recommendations, curated playlists, and promotional strategies. Genres with high average play counts may indicate strong listener retention, while those with lower engagement may require better discovery features or targeted marketing.

<img width="627" alt="Screenshot 2025-03-18 at 11 12 41 PM" src="https://github.com/user-attachments/assets/5a492499-766f-4fb1-b301-aafb2a59eb47" />


TPQ_10 : Write a query to list the most popular artists in each genre if their album has more than 10 tracks and they are from where the genre originated. List the artist name, genre name, and genre origin country.

Description: This query identifies the most popular artists in each genre if they have an album with more than 10 tracks and are from the genre’s origin country. It highlights authentic and prolific contributors, helping streaming platforms promote culturally significant artists. This insight supports playlist curation, regional marketing, and event planning, ensuring users discover genre-defining musicians while boosting engagement and targeted promotions.

<img width="625" alt="Screenshot 2025-03-18 at 11 12 29 PM" src="https://github.com/user-attachments/assets/16b083cb-ae05-4a86-96d5-de8c82e855ad" />




## Query Complexity Matrix
<img width="628" alt="Screenshot 2025-03-18 at 11 00 01 PM" src="https://github.com/user-attachments/assets/11934eaa-21a0-43b9-af38-70c3fc38db38" />


