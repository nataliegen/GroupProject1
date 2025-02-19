# GroupProject1

Web Player
<img width="1512" alt="Screenshot 2025-02-19 at 9 26 06 AM" src="https://github.com/user-attachments/assets/418b568e-a5de-45d7-b5b4-9e0e5135f472" />


**Users** - Stores user details with a unique user_ID.

Relationships:
-  One-to-Many with MusicLibraries (each user can have many libraries).
-  One-to-Many with Playlists (each user can create multiple playlists).
-  One-to-Many with PlayerSessions (each user can have multiple listening sessions).


**MusicLibraries** - Represents a user's music collection.

Relationships:
-  Many-to-Many with Songs via LibrarySongs (each library can contain multiple songs).

**PlaylistSongs** - Allows users to have multiple songs in their library while each song can belong to multiple libraries.

**Songs** - Contains song data

Relationships:
-  One-to-Many with PlayCounts (each song can have multiple play records).
-  Many-to-Many with Playlists via PlaylistSongs (a song can be in multiple playlists).
-  Many-to-Many with Genres via SongGenres (a song can belong to multiple genres).


**PlayerSessions** - Tracks user sessions.

Relationships:
One-to-Many with Users (a user can have multiple sessions).
Each session tracks a single song being played.


**Playlists** - Represents playlists.

Relationships:
-  One-to-Many with Users (a user can have multiple playlists).
-  Many-to-Many with Songs via PlaylistSongs.

**PlaylistSongs** - Connects Playlists and Songs in a Many-to-Many relationship.


**PlayCounts** - Tracks how many times a song has been played.

Relationships:
-  One-to-Many with Songs (a song can have multiple play counts).
-  One-to-Many with TopFiveSongs (ranking popular songs).


**TopFiveSongs** - Stores the top five songs from play count.

Relationships:
- One-to-Many with PlayCounts (each top song is linked to a play count record).

**Genres** - Stores music genres.
Relationships:
-  Many-to-Many with Songs via SongGenres.


**SongGenres** Connects Songs and Genres in a Many-to-Many relationship.
