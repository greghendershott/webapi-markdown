# last.fm non-authenticated API

See <http://www.last.fm/api/intro>.

This file defines only _anonymous_ services.

Endpoint: http://ws.audioscrobbler.com

# Chart

Get various things from the chart.

## Request:

````
GET /2.0/
    ?method={}
    &api_key={api-key}
    &format=json
    &[page=1]
    &[limit=50]
````

 `method` can be:
- `chart.getHypedArtists`
- `chart.getHypedTracks`
- `chart.getLovedTracks`
- `chart.getTopArtists`
- `chart.getTopTags`
- `chart.getTopTracks`

# Artist

## Request
````
GET /2.0/
    ?method={}
    &artist={}
    &[mbid={}]
    &api_key={api-key}
    &format=json
    &[limit=50]
    &[page=1]
    &[autocorrect={}]
    &[festivalsonly={}]
````

 `method` can be:
- `artist.getEvents`
- `aritst.getInfo`
- `artist.getPastEvents`
- `artist.getPodcast`
- `artist.getShouts`
- `artist.getSimilar`
- `artist.getTags`
- `artist.getTopAlbums`
- `artist.getTopFans`
- `artist.getTopTags`
- `artist.getTopTracks`

# Album

## Request
````
GET /2.0/
    ?format=json
    &method={}
    &artist={}
    &album={}
    &[mbid={}]
    &[country={}]
    &api_key={api-key}
    &[limit=50]
    &[page=1]
    &[autocorrect={}]
````

 `method` can be:
- `album.getBuyLinks`
- `album.getInfo`
- `album.getShouts`
- `album.getTags`
- `album.getTopTags`

# Event

## Request
````
GET /2.0/
    ?format=json
    &method={}
    &event={}
    &api_key={api-key}
    &[limit=50]
    &[page=1]
````

 `method` can be:
- `event.getAttendees`
- `event.getInfo`
- `event.getShouts`

# User

## Request

````
GET /2.0/
    ?format=json
    &method={}
    &user={}
    &[artist={}]
    &[startTimestamp={}]
    &[endTimestamp={}]
    &[page=1]
    &[limit={}]
    &api_key={api-key}
````

`startTimestamp` and `endTimestamp` are
[UNIX timestamps](http://en.wikipedia.org/wiki/Unix_time).

 `method` can be:
- `user.getArtistTracks`
- `user.getBannedTracks`
- `user.getEvents`
- `user.getFriends`
- `user.getInfo`
- `user.getLovedTracks`
- `user.getNeighbours`
- `user.getNewReleases`
- `user.getPastEvents`
- `user.getPersonalTags`
- `user.getPlaylists`
- `user.getRecentStations`
- `user.getRecentTracks`
- `user.getRecommendedArtists`
- `user.getRecommendedEvents`
- `user.getShouts`
- `user.getTopAlbums`
- `user.getTopArtists`
- `user.getTopTags`
- `user.getTopTracks`
- `user.getWeeklyAlbumChart`
- `user.getWeeklyArtistChart`
- `user.getWeeklyChartList`
- `user.getWeeklyTrackChart`
