
###  Supported Subsonic API endpoints

CloudSonic is currently compatible (to some extent) with [Subsonic API](subsonic.org/pages/api.jsp) v1.8.0, with some exceptions.

This is an (almost) up to date list of all Subsonic API endpoints implemented by CloudSonic. 
Check the "Notes" column for limitations/missing behaviour. Also keep in mind these differences between 
CloudSonic and Subsonic:

* Right now, CloudSonic only works with a single Music Library (Music Folder)
* CloudSonic does not mark songs as played by calls to `stream`, only when 
 `scrobble` is called with `submission=true`
* Next features to be implemented: Playlists (WIP), MultiUser (WIP), Jukebox, Sharing, Podcasts, Bookmarks, Internet Radio. 


| ENDPOINT               | NOTES |
|------------------------|-------|
| _SYSTEM_               ||
| `ping`                 | |
| `getLicense`           | Always valid ;) |    
| ||
| _BROWSING_             ||
| `getMusicFolders`      | Hardcoded to just one, configured in `app.conf` |
| `getIndexes`           | Doesn't support shortcuts, nor direct children |
| `getMusicDirectory`    | |
| `getSong`              | |
| `getArtists`           | |
| `getArtist`            | |
| `getAlbum`             | |
| `getGenres`            | |
| ||
| _ALBUM/SONGS LISTS_    ||
| `getAlbumList`         | `byYear` and `byGenre` are not implemented |
| `getAlbumList2`        | `byYear` and `byGenre` are not implemented |
| `getStarred`           | |
| `getStarred2`          | |
| `getNowPlaying`        | |
| `getRandomSongs`       | Ignores `year` parameter |
| ||
| _SEARCHING_            ||
| `search2`              | Doesn't support Lucene queries, only simple auto complete queries |
| `search3`              | Doesn't support Lucene queries, only simple auto complete queries |
| ||
| _PLAYLISTS_            ||
| `getPlaylists`         | `username` parameter is not implemented |
| `getPlaylist`          | |
| `createPlaylist`       | Return empty response on success |
| `updatePlaylist`       | `comment` and `public` are not implemented |
| `deletePlaylist`       | |
| ||
| _MEDIA RETRIEVAL_      ||
| `stream`               | Returns wrong content-length when downsampling |
| `download`             | |
| `getCoverArt`          | Only gets embedded artwork |
| `getAvatar`            | Always returns the same image |
| ||
| _MEDIA ANNOTATION_     ||
| `star`                 | |
| `unstar`               | |
| `setRating`            | Doesn't work with artists |
| `scrobble`             | No Last.FM support yet. It is used to update play count, last played, skip count and last skipped |
| ||
| _USER MANAGEMENT_      ||
| `getUser`              | Hardcoded all roles, ignores `username` parameter|