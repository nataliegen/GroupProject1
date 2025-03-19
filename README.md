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

![PNG image](https://github.com/user-attachments/assets/210eeb6c-258c-4c4a-aba7-0cc9af91863f)


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

**MusicLibrary** – Represents a user's music collection
Attributes:
- Primary Key: libraryID
- Foreign Key: userID
- songID
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
- One-to-Many with Albums (an artist can have multiple albums).

**Album** – Stores information about albums
Attributes:
- Primary Key: albumID
- Foreign Key: artistID
- title
- release_date
- record_label
- total_tracks
- duration
- album_type

**Relationships**:
- One-to-Many with Songs (each album contains multiple songs).

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
- playlist_last_played_date
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
![Screenshot 2025-03-17 114233](https://github.com/user-attachments/assets/02842a88-81a0-4e84-9d53-9f3999196585)
![Screenshot 2025-03-17 114304](https://github.com/user-attachments/assets/38a7ab9b-6f22-41a3-a507-b37f63473469)
![Screenshot 2025-03-17 114324](https://github.com/user-attachments/assets/fb8498ad-ceed-453f-89f1-225e96f22adf)
![Screenshot 2025-03-17 114339](https://github.com/user-attachments/assets/9e9ef908-049c-42fc-8338-75921d72e88d)
![Screenshot 2025-03-17 114355](https://github.com/user-attachments/assets/1343f9f7-be7d-4143-ab6f-5ade73669aa4)

##Query Complexity Matrix
<img width="627" alt="Screenshot 2025-03-18 at 10 48 35 PM" src="https://github.com/user-attachments/assets/526bcc74-9834-4293-b550-b25b714f614a" />

