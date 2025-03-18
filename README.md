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
Web Player
<img width="1239" alt="Screenshot 2025-03-18 at 1 49 01 PM" src="https://github.com/user-attachments/assets/4994ddc9-fb95-4468-b72d-5f5204154d12" />


**Users** - Stores user details with a unique user_ID.

Relationships:
-  One-to-Many with MusicLibraries (each user can have many libraries).
-  One-to-Many with Playlists (each user can create multiple playlists).
-  One-to-Many with PlayerSessions (each user can have multiple listening sessions).


**MusicLibraries** - Represents a user's music collection.

Relationships:
-  Many-to-Many with Songs via LibrarySongs (each library can contain multiple songs).

**LibrarySongs** - Allows users to have multiple songs in their library while each song can belong to multiple libraries.

**Songs** - Contains song data

Relationships:
-  One-to-Many with PlayCounts (each song can have multiple play records).
-  Many-to-Many with Playlists via PlaylistSongs (a song can be in multiple playlists).
-  Many-to-Many with Genres via SongGenres (a song can belong to multiple genres).
-  Many-to-Many with MusicLibraries via LibrarySongs.

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

-  Many-to-Many with Songs via SongGenres.


**SongGenres** Connects Songs and Genres in a Many-to-Many relationship.


## Data Dictionary 
![Screenshot 2025-03-17 114233](https://github.com/user-attachments/assets/02842a88-81a0-4e84-9d53-9f3999196585)
![Screenshot 2025-03-17 114304](https://github.com/user-attachments/assets/38a7ab9b-6f22-41a3-a507-b37f63473469)
![Screenshot 2025-03-17 114324](https://github.com/user-attachments/assets/fb8498ad-ceed-453f-89f1-225e96f22adf)
![Screenshot 2025-03-17 114339](https://github.com/user-attachments/assets/9e9ef908-049c-42fc-8338-75921d72e88d)
![Screenshot 2025-03-17 114355](https://github.com/user-attachments/assets/1343f9f7-be7d-4143-ab6f-5ade73669aa4)
