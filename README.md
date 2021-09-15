# React Part Time Class Final Project - Spotify Recommendation App

## Project Links

TODO 
- [CodeSandbox Link]() - Will add once project build has started.

## Project Description

This react app logs into a user's Spotify account via the [Spotify API](https://developer.spotify.com/documentation/web-api/reference/) and retrieves recently played tracks. The user can select a track and the app will pull the artist id, song id, and retrieve the genres associated with the artist and return a selection of recommended tracks based on the `/get-recommendations/` API endpoint.


## Wireframes
- [Login Screen](https://res.cloudinary.com/dso47oeq6/image/upload/v1631711776/Login_Screen_omvs84.jpg) - prompts the user for a user/pass combo and uses that data, along with the app id and secret to login.

- [Recently Played Tracks](https://res.cloudinary.com/dso47oeq6/image/upload/v1631711785/Recently_Played_Tracks_rfxdy7.jpg) - once user is logged in the app will make an API call to `/v1/me/player/recently-played` to get the users most recently played tracks.
- [Recommendation Form](https://res.cloudinary.com/dso47oeq6/image/upload/v1631711792/Recommendation_Form_maauta.jpg) -  - this is a post MVP reach. The form allows the user to provide filters, in addition to artist, song and genre, to get more granular results.
- [Recommended Tracks](https://res.cloudinary.com/dso47oeq6/image/upload/v1631711800/Returned_Recommended_Tracks_nmkx9j.jpg) -  - the returned results from `get-recommendations` API endpoint
- [React Architecture Mock Up](https://res.cloudinary.com/dso47oeq6/image/upload/v1631750363/react-app-arch_n6smst.ai) 

#### MVP EXAMPLE
- App home page - prompts user login and uses Spotify auth flow to gather user credentails, validate and then return an auth token. Token will be saved in state for reuse throughout the App lifecycle (or until token expires).
- Post login - page displaying 10 most recently played tracks (data retrieved by app after successful login)
- Ability for user to click on a track and use the artist id, song id, and related genres associated with track to pull a list of recommendations.
- Recommendations page - displays a list of recommended songs (max 10) based on API call initiated by user click on recently played tracks page.

#### PostMVP EXAMPLE

- Add form to allow user to further filter results based on additional paremeters - ex: tempo, danceability, energy, loudness
- Ability for users to save recommended tracks via API endpoint `/v1/me/tracks`
- Ability to play recommended tracks using spotify Web Playback SDK - `https://developer.spotify.com/documentation/web-playback-sdk/`

## API

This project will make use of a few different API endpoints available from the Spotify 

### Authorize (login) `https://accounts.spotify.com/authorize`

- Required params
	- client_id 
	- response_type - should be set to code
	- redirect_uri - app page uri to redirect to when login is successful 


### Recently Played Tracks - `	/v1/me/player/recently-played`

- Required params
	- none 

- Returns an array of recently played tracks. Number returned can be set. Default is 10. The returned data also includes pagination links for the next 10 or, if applicable, the previous 10.

- Required params
	- seed_artists - a comma separated list of artist ids
	- seed_genres - a comma separated list of genre names ex: clasical,country
	- seed_tracks - a comma separated list of track ids


```
{items: [
	{
		"track": {
        "album": {
          "album_type": "album",
          "artists": [
            {
              "external_urls": {
                "spotify": "https://open.spotify.com/artist/5Wabl1lPdNOeIn0SQ5A1mp"
              },
              "href": "https://api.spotify.com/v1/artists/5Wabl1lPdNOeIn0SQ5A1mp",
              "id": "5Wabl1lPdNOeIn0SQ5A1mp",
              "name": "Cocteau Twins",
              "type": "artist",
              "uri": "spotify:artist:5Wabl1lPdNOeIn0SQ5A1mp"
            }
          ],
          "available_markets": [
            "AD",
            "AE",
            "AG",
            "AL",
            "AM",
            "AO",
            "AR",
            "AT",
            "AU",
            "AZ",
            "BA",
            "BB",
            "BD",
            "BE",
            "BF",
            "BG",
            "BH",
            "BI",
            "BJ",
            "BN",
            "BO",
            "BR",
            "BS",
            "BT",
            "BW",
            "BY",
            "BZ",
            "CA",
            "CH",
            "CI",
            "CL",
            "CM",
            "CO",
            "CR",
            "CV",
            "CW",
            "CY",
            "CZ",
            "DE",
            "DJ",
            "DK",
            "DM",
            "DO",
            "DZ",
            "EC",
            "EE",
            "EG",
            "ES",
            "FI",
            "FJ",
            "FM",
            "FR",
            "GA",
            "GB",
            "GD",
            "GE",
            "GH",
            "GM",
            "GN",
            "GQ",
            "GR",
            "GT",
            "GW",
            "GY",
            "HK",
            "HN",
            "HR",
            "HT",
            "HU",
            "ID",
            "IE",
            "IL",
            "IN",
            "IS",
            "IT",
            "JM",
            "JO",
            "JP",
            "KE",
            "KG",
            "KH",
            "KI",
            "KM",
            "KN",
            "KR",
            "KW",
            "KZ",
            "LA",
            "LB",
            "LC",
            "LI",
            "LK",
            "LR",
            "LS",
            "LT",
            "LU",
            "LV",
            "MA",
            "MC",
            "MD",
            "ME",
            "MG",
            "MH",
            "MK",
            "ML",
            "MN",
            "MO",
            "MR",
            "MT",
            "MU",
            "MV",
            "MW",
            "MX",
            "MY",
            "MZ",
            "NA",
            "NE",
            "NG",
            "NI",
            "NL",
            "NO",
            "NP",
            "NR",
            "NZ",
            "OM",
            "PA",
            "PE",
            "PG",
            "PH",
            "PK",
            "PL",
            "PS",
            "PT",
            "PW",
            "PY",
            "QA",
            "RO",
            "RS",
            "RU",
            "RW",
            "SA",
            "SB",
            "SC",
            "SE",
            "SG",
            "SI",
            "SK",
            "SL",
            "SM",
            "SN",
            "SR",
            "ST",
            "SV",
            "SZ",
            "TD",
            "TG",
            "TH",
            "TL",
            "TN",
            "TO",
            "TR",
            "TT",
            "TV",
            "TW",
            "TZ",
            "UA",
            "UG",
            "US",
            "UY",
            "UZ",
            "VC",
            "VN",
            "VU",
            "WS",
            "XK",
            "ZA",
            "ZM",
            "ZW"
          ],
          "external_urls": {
            "spotify": "https://open.spotify.com/album/6dFmNBt5ZLbaqf7PCtuvUv"
          },
          "href": "https://api.spotify.com/v1/albums/6dFmNBt5ZLbaqf7PCtuvUv",
          "id": "6dFmNBt5ZLbaqf7PCtuvUv",
          "images": [
            {
              "height": 640,
              "url": "https://i.scdn.co/image/ab67616d0000b273f5947222ca227a92c6d6ced7",
              "width": 640
            },
            {
              "height": 300,
              "url": "https://i.scdn.co/image/ab67616d00001e02f5947222ca227a92c6d6ced7",
              "width": 300
            },
            {
              "height": 64,
              "url": "https://i.scdn.co/image/ab67616d00004851f5947222ca227a92c6d6ced7",
              "width": 64
            }
          ],
          "name": "Victorialand",
          "release_date": "1986-04-14",
          "release_date_precision": "day",
          "total_tracks": 9,
          "type": "album",
          "uri": "spotify:album:6dFmNBt5ZLbaqf7PCtuvUv"
        },
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/5Wabl1lPdNOeIn0SQ5A1mp"
            },
            "href": "https://api.spotify.com/v1/artists/5Wabl1lPdNOeIn0SQ5A1mp",
            "id": "5Wabl1lPdNOeIn0SQ5A1mp",
            "name": "Cocteau Twins",
            "type": "artist",
            "uri": "spotify:artist:5Wabl1lPdNOeIn0SQ5A1mp"
          }
        ],
        "available_markets": [
          "AD",
          "AE",
          "AG",
          "AL",
          "AM",
          "AO",
          "AR",
          "AT",
          "AU",
          "AZ",
          "BA",
          "BB",
          "BD",
          "BE",
          "BF",
          "BG",
          "BH",
          "BI",
          "BJ",
          "BN",
          "BO",
          "BR",
          "BS",
          "BT",
          "BW",
          "BY",
          "BZ",
          "CA",
          "CH",
          "CI",
          "CL",
          "CM",
          "CO",
          "CR",
          "CV",
          "CW",
          "CY",
          "CZ",
          "DE",
          "DJ",
          "DK",
          "DM",
          "DO",
          "DZ",
          "EC",
          "EE",
          "EG",
          "ES",
          "FI",
          "FJ",
          "FM",
          "FR",
          "GA",
          "GB",
          "GD",
          "GE",
          "GH",
          "GM",
          "GN",
          "GQ",
          "GR",
          "GT",
          "GW",
          "GY",
          "HK",
          "HN",
          "HR",
          "HT",
          "HU",
          "ID",
          "IE",
          "IL",
          "IN",
          "IS",
          "IT",
          "JM",
          "JO",
          "JP",
          "KE",
          "KG",
          "KH",
          "KI",
          "KM",
          "KN",
          "KR",
          "KW",
          "KZ",
          "LA",
          "LB",
          "LC",
          "LI",
          "LK",
          "LR",
          "LS",
          "LT",
          "LU",
          "LV",
          "MA",
          "MC",
          "MD",
          "ME",
          "MG",
          "MH",
          "MK",
          "ML",
          "MN",
          "MO",
          "MR",
          "MT",
          "MU",
          "MV",
          "MW",
          "MX",
          "MY",
          "MZ",
          "NA",
          "NE",
          "NG",
          "NI",
          "NL",
          "NO",
          "NP",
          "NR",
          "NZ",
          "OM",
          "PA",
          "PE",
          "PG",
          "PH",
          "PK",
          "PL",
          "PS",
          "PT",
          "PW",
          "PY",
          "QA",
          "RO",
          "RS",
          "RU",
          "RW",
          "SA",
          "SB",
          "SC",
          "SE",
          "SG",
          "SI",
          "SK",
          "SL",
          "SM",
          "SN",
          "SR",
          "ST",
          "SV",
          "SZ",
          "TD",
          "TG",
          "TH",
          "TL",
          "TN",
          "TO",
          "TR",
          "TT",
          "TV",
          "TW",
          "TZ",
          "UA",
          "UG",
          "US",
          "UY",
          "UZ",
          "VC",
          "VN",
          "VU",
          "WS",
          "XK",
          "ZA",
          "ZM",
          "ZW"
        ],
        "disc_number": 1,
        "duration_ms": 206333,
        "explicit": false,
        "external_ids": {
          "isrc": "GBAFL8600041"
        },
        "external_urls": {
          "spotify": "https://open.spotify.com/track/02Rc5AYX43X72b3PPYbhN7"
        },
        "href": "https://api.spotify.com/v1/tracks/02Rc5AYX43X72b3PPYbhN7",
        "id": "02Rc5AYX43X72b3PPYbhN7",
        "is_local": false,
        "name": "Feet-like Fins",
        "popularity": 27,
        "preview_url": "https://p.scdn.co/mp3-preview/45f9aa56d45505bb1cf6be1c266d946bc83bee29?cid=774b29d4f13844c495f206cafdad9c86",
        "track_number": 7,
        "type": "track",
        "uri": "spotify:track:02Rc5AYX43X72b3PPYbhN7"
      },
      "played_at": "2021-09-11T17:47:02.473Z",
      "context": {
        "external_urls": {
          "spotify": "https://open.spotify.com/playlist/13TlZYPj9XfPnFrb0qZtRT"
        },
        "href": "https://api.spotify.com/v1/playlists/13TlZYPj9XfPnFrb0qZtRT",
        "type": "playlist",
        "uri": "spotify:playlist:13TlZYPj9XfPnFrb0qZtRT"
      }
    },
	}
]  }
```
### Recommendations -  `/v1/recommendations`
```
{
  "tracks": [
    {
      "album": {
        "album_type": "COMPILATION",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/0LyfQWJT6nXafLPZqxe9Of"
            },
            "href": "https://api.spotify.com/v1/artists/0LyfQWJT6nXafLPZqxe9Of",
            "id": "0LyfQWJT6nXafLPZqxe9Of",
            "name": "Various Artists",
            "type": "artist",
            "uri": "spotify:artist:0LyfQWJT6nXafLPZqxe9Of"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/6lJrqUXdCpEINx1fi5EqMa"
        },
        "href": "https://api.spotify.com/v1/albums/6lJrqUXdCpEINx1fi5EqMa",
        "id": "6lJrqUXdCpEINx1fi5EqMa",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b27333d6ad1275ae8ebe156686f5",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e0233d6ad1275ae8ebe156686f5",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d0000485133d6ad1275ae8ebe156686f5",
            "width": 64
          }
        ],
        "name": "The Twilight Saga: Breaking Dawn - Part 2 (Original Motion Picture Soundtrack)",
        "release_date": "2012-11-09",
        "release_date_precision": "day",
        "total_tracks": 14,
        "type": "album",
        "uri": "spotify:album:6lJrqUXdCpEINx1fi5EqMa"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/0SbSDzM4X41hnlURed0fcV"
          },
          "href": "https://api.spotify.com/v1/artists/0SbSDzM4X41hnlURed0fcV",
          "id": "0SbSDzM4X41hnlURed0fcV",
          "name": "Carter Burwell",
          "type": "artist",
          "uri": "spotify:artist:0SbSDzM4X41hnlURed0fcV"
        }
      ],
      "disc_number": 1,
      "duration_ms": 255773,
      "explicit": false,
      "external_ids": {
        "isrc": "USAT21206056"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/1brH9m4Q2LHTuwxaKoMTn5"
      },
      "href": "https://api.spotify.com/v1/tracks/1brH9m4Q2LHTuwxaKoMTn5",
      "id": "1brH9m4Q2LHTuwxaKoMTn5",
      "is_local": false,
      "is_playable": true,
      "name": "Plus Que Ma Prope Vie",
      "popularity": 49,
      "preview_url": "https://p.scdn.co/mp3-preview/9e14846e6f60448e7a07e5430dd8bc09d1858d5c?cid=774b29d4f13844c495f206cafdad9c86",
      "track_number": 14,
      "type": "track",
      "uri": "spotify:track:1brH9m4Q2LHTuwxaKoMTn5"
    },
    {
      "album": {
        "album_type": "COMPILATION",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/0LyfQWJT6nXafLPZqxe9Of"
            },
            "href": "https://api.spotify.com/v1/artists/0LyfQWJT6nXafLPZqxe9Of",
            "id": "0LyfQWJT6nXafLPZqxe9Of",
            "name": "Various Artists",
            "type": "artist",
            "uri": "spotify:artist:0LyfQWJT6nXafLPZqxe9Of"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/2Re6RMBEfD8iv1HMxLMdzI"
        },
        "href": "https://api.spotify.com/v1/albums/2Re6RMBEfD8iv1HMxLMdzI",
        "id": "2Re6RMBEfD8iv1HMxLMdzI",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b2732b4d071f7824b2c60c3b85cd",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e022b4d071f7824b2c60c3b85cd",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d000048512b4d071f7824b2c60c3b85cd",
            "width": 64
          }
        ],
        "name": "The Lord of the Rings - The Return of the King - The Complete Recordings (Limited Edition)",
        "release_date": "2003-11-24",
        "release_date_precision": "day",
        "total_tracks": 53,
        "type": "album",
        "uri": "spotify:album:2Re6RMBEfD8iv1HMxLMdzI"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/0OcclcP5o8VKH2TRqSY2A7"
          },
          "href": "https://api.spotify.com/v1/artists/0OcclcP5o8VKH2TRqSY2A7",
          "id": "0OcclcP5o8VKH2TRqSY2A7",
          "name": "Howard Shore",
          "type": "artist",
          "uri": "spotify:artist:0OcclcP5o8VKH2TRqSY2A7"
        }
      ],
      "disc_number": 1,
      "duration_ms": 738080,
      "explicit": false,
      "external_ids": {
        "isrc": "USRE10701458"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/1lIcdDpGlc2mO2LYA0f5KM"
      },
      "href": "https://api.spotify.com/v1/tracks/1lIcdDpGlc2mO2LYA0f5KM",
      "id": "1lIcdDpGlc2mO2LYA0f5KM",
      "is_local": false,
      "is_playable": true,
      "name": "The Fellowship Reunited (feat. Sir James Galway, Viggo Mortensen and Renée Fleming)",
      "popularity": 50,
      "preview_url": "https://p.scdn.co/mp3-preview/037cbcc8f72c18f542b982b9235ed91b2aa6e9b5?cid=774b29d4f13844c495f206cafdad9c86",
      "track_number": 49,
      "type": "track",
      "uri": "spotify:track:1lIcdDpGlc2mO2LYA0f5KM"
    },
    {
      "album": {
        "album_type": "ALBUM",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/13Of0gTz6vyIphtPBPgOYh"
            },
            "href": "https://api.spotify.com/v1/artists/13Of0gTz6vyIphtPBPgOYh",
            "id": "13Of0gTz6vyIphtPBPgOYh",
            "name": "Nikolai Tokarev",
            "type": "artist",
            "uri": "spotify:artist:13Of0gTz6vyIphtPBPgOYh"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/5lpfGaObTKMHdZ4iQZFWnw"
            },
            "href": "https://api.spotify.com/v1/artists/5lpfGaObTKMHdZ4iQZFWnw",
            "id": "5lpfGaObTKMHdZ4iQZFWnw",
            "name": "Giuseppe Andaloro",
            "type": "artist",
            "uri": "spotify:artist:5lpfGaObTKMHdZ4iQZFWnw"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/33zC4jWgBRURDclBVL7F9W"
            },
            "href": "https://api.spotify.com/v1/artists/33zC4jWgBRURDclBVL7F9W",
            "id": "33zC4jWgBRURDclBVL7F9W",
            "name": "Herbert Schuch",
            "type": "artist",
            "uri": "spotify:artist:33zC4jWgBRURDclBVL7F9W"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/19oxtDOnRGGA3qsQF6I7e3"
            },
            "href": "https://api.spotify.com/v1/artists/19oxtDOnRGGA3qsQF6I7e3",
            "id": "19oxtDOnRGGA3qsQF6I7e3",
            "name": "Robert Levin",
            "type": "artist",
            "uri": "spotify:artist:19oxtDOnRGGA3qsQF6I7e3"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/2dwgNdwwrqJiKJwDdz8IP3"
            },
            "href": "https://api.spotify.com/v1/artists/2dwgNdwwrqJiKJwDdz8IP3",
            "id": "2dwgNdwwrqJiKJwDdz8IP3",
            "name": "Vladimir Kharin",
            "type": "artist",
            "uri": "spotify:artist:2dwgNdwwrqJiKJwDdz8IP3"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/14S84oRhjPyiff7zhRWRzr"
        },
        "href": "https://api.spotify.com/v1/albums/14S84oRhjPyiff7zhRWRzr",
        "id": "14S84oRhjPyiff7zhRWRzr",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b273ca5b1b904a82a9c5e65e8384",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e02ca5b1b904a82a9c5e65e8384",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d00004851ca5b1b904a82a9c5e65e8384",
            "width": 64
          }
        ],
        "name": "Variations (Edition Ruhr Piano Festival, Vol. 14)",
        "release_date": "2006",
        "release_date_precision": "year",
        "total_tracks": 6,
        "type": "album",
        "uri": "spotify:album:14S84oRhjPyiff7zhRWRzr"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/1C3sffOOvQNUwg4YIsvKqy"
          },
          "href": "https://api.spotify.com/v1/artists/1C3sffOOvQNUwg4YIsvKqy",
          "id": "1C3sffOOvQNUwg4YIsvKqy",
          "name": "César Franck",
          "type": "artist",
          "uri": "spotify:artist:1C3sffOOvQNUwg4YIsvKqy"
        },
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/5lpfGaObTKMHdZ4iQZFWnw"
          },
          "href": "https://api.spotify.com/v1/artists/5lpfGaObTKMHdZ4iQZFWnw",
          "id": "5lpfGaObTKMHdZ4iQZFWnw",
          "name": "Giuseppe Andaloro",
          "type": "artist",
          "uri": "spotify:artist:5lpfGaObTKMHdZ4iQZFWnw"
        }
      ],
      "disc_number": 1,
      "duration_ms": 830493,
      "explicit": false,
      "external_ids": {
        "isrc": "DEAQ70500866"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/7ivXObFl4X6vZUa4cKgApz"
      },
      "href": "https://api.spotify.com/v1/tracks/7ivXObFl4X6vZUa4cKgApz",
      "id": "7ivXObFl4X6vZUa4cKgApz",
      "is_local": false,
      "is_playable": true,
      "name": "Prélude, Fugue and Variation in B Minor for Organ, FWV 30, Op. 18: Prélude, Fugue and Variation in B Minor for Organ, FWV 30, Op. 18 - Live",
      "popularity": 22,
      "preview_url": "https://p.scdn.co/mp3-preview/a6fe8f05be2be88511b4901775a457df65b66043?cid=774b29d4f13844c495f206cafdad9c86",
      "track_number": 4,
      "type": "track",
      "uri": "spotify:track:7ivXObFl4X6vZUa4cKgApz"
    },
    {
      "album": {
        "album_type": "SINGLE",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/1nIUhcKHnK6iyumRyoV68C"
            },
            "href": "https://api.spotify.com/v1/artists/1nIUhcKHnK6iyumRyoV68C",
            "id": "1nIUhcKHnK6iyumRyoV68C",
            "name": "Ennio Morricone",
            "type": "artist",
            "uri": "spotify:artist:1nIUhcKHnK6iyumRyoV68C"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/5mdimgZkyNZRMFfogxjnDs"
        },
        "href": "https://api.spotify.com/v1/albums/5mdimgZkyNZRMFfogxjnDs",
        "id": "5mdimgZkyNZRMFfogxjnDs",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b273311a5ea3f35335c1fd731a30",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e02311a5ea3f35335c1fd731a30",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d00004851311a5ea3f35335c1fd731a30",
            "width": 64
          }
        ],
        "name": "The Ecstasy of Gold (From \"The Good, The Bad and The Ugly\") - Single",
        "release_date": "1966",
        "release_date_precision": "year",
        "total_tracks": 1,
        "type": "album",
        "uri": "spotify:album:5mdimgZkyNZRMFfogxjnDs"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/1nIUhcKHnK6iyumRyoV68C"
          },
          "href": "https://api.spotify.com/v1/artists/1nIUhcKHnK6iyumRyoV68C",
          "id": "1nIUhcKHnK6iyumRyoV68C",
          "name": "Ennio Morricone",
          "type": "artist",
          "uri": "spotify:artist:1nIUhcKHnK6iyumRyoV68C"
        },
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/44oCA91Zsi73fzubIX6Sqh"
          },
          "href": "https://api.spotify.com/v1/artists/44oCA91Zsi73fzubIX6Sqh",
          "id": "44oCA91Zsi73fzubIX6Sqh",
          "name": "Edda Dell'Orso",
          "type": "artist",
          "uri": "spotify:artist:44oCA91Zsi73fzubIX6Sqh"
        }
      ],
      "disc_number": 1,
      "duration_ms": 203066,
      "explicit": false,
      "external_ids": {
        "isrc": "ITC460500468"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/68oxELAW6URbwJCKmBiNDa"
      },
      "href": "https://api.spotify.com/v1/tracks/68oxELAW6URbwJCKmBiNDa",
      "id": "68oxELAW6URbwJCKmBiNDa",
      "is_local": false,
      "is_playable": true,
      "name": "The Ecstasy of Gold - L'Estasi Dell'oro",
      "popularity": 30,
      "preview_url": "https://p.scdn.co/mp3-preview/fc9dd7923ee63e8ce581daca511e30211cb200db?cid=774b29d4f13844c495f206cafdad9c86",
      "track_number": 1,
      "type": "track",
      "uri": "spotify:track:68oxELAW6URbwJCKmBiNDa"
    },
    {
      "album": {
        "album_type": "ALBUM",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/1KP6TWI40m7p3QBTU6u2xo"
            },
            "href": "https://api.spotify.com/v1/artists/1KP6TWI40m7p3QBTU6u2xo",
            "id": "1KP6TWI40m7p3QBTU6u2xo",
            "name": "BØRNS",
            "type": "artist",
            "uri": "spotify:artist:1KP6TWI40m7p3QBTU6u2xo"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/17l7MIu0Jh0tdgK7or9ovw"
        },
        "href": "https://api.spotify.com/v1/albums/17l7MIu0Jh0tdgK7or9ovw",
        "id": "17l7MIu0Jh0tdgK7or9ovw",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b273cc2cf912462d8ae4ef856434",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e02cc2cf912462d8ae4ef856434",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d00004851cc2cf912462d8ae4ef856434",
            "width": 64
          }
        ],
        "name": "Dopamine",
        "release_date": "2015-10-16",
        "release_date_precision": "day",
        "total_tracks": 11,
        "type": "album",
        "uri": "spotify:album:17l7MIu0Jh0tdgK7or9ovw"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/1KP6TWI40m7p3QBTU6u2xo"
          },
          "href": "https://api.spotify.com/v1/artists/1KP6TWI40m7p3QBTU6u2xo",
          "id": "1KP6TWI40m7p3QBTU6u2xo",
          "name": "BØRNS",
          "type": "artist",
          "uri": "spotify:artist:1KP6TWI40m7p3QBTU6u2xo"
        }
      ],
      "disc_number": 1,
      "duration_ms": 174693,
      "explicit": false,
      "external_ids": {
        "isrc": "USUM71413949"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/2pA4ip3VIEVcIa3qE02oAX"
      },
      "href": "https://api.spotify.com/v1/tracks/2pA4ip3VIEVcIa3qE02oAX",
      "id": "2pA4ip3VIEVcIa3qE02oAX",
      "is_local": false,
      "is_playable": true,
      "name": "10,000 Emerald Pools",
      "popularity": 63,
      "preview_url": null,
      "track_number": 1,
      "type": "track",
      "uri": "spotify:track:2pA4ip3VIEVcIa3qE02oAX"
    },
    {
      "album": {
        "album_type": "SINGLE",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/4WN5naL3ofxrVBgFpguzKo"
            },
            "href": "https://api.spotify.com/v1/artists/4WN5naL3ofxrVBgFpguzKo",
            "id": "4WN5naL3ofxrVBgFpguzKo",
            "name": "Rudimental",
            "type": "artist",
            "uri": "spotify:artist:4WN5naL3ofxrVBgFpguzKo"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/5hAJKdlLfFblwwmGR0a3Lk"
        },
        "href": "https://api.spotify.com/v1/albums/5hAJKdlLfFblwwmGR0a3Lk",
        "id": "5hAJKdlLfFblwwmGR0a3Lk",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b2735530d21cddc71a77530dd6c4",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e025530d21cddc71a77530dd6c4",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d000048515530d21cddc71a77530dd6c4",
            "width": 64
          }
        ],
        "name": "Feel the Love (feat. John Newman)",
        "release_date": "2012-06-12",
        "release_date_precision": "day",
        "total_tracks": 5,
        "type": "album",
        "uri": "spotify:album:5hAJKdlLfFblwwmGR0a3Lk"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/4WN5naL3ofxrVBgFpguzKo"
          },
          "href": "https://api.spotify.com/v1/artists/4WN5naL3ofxrVBgFpguzKo",
          "id": "4WN5naL3ofxrVBgFpguzKo",
          "name": "Rudimental",
          "type": "artist",
          "uri": "spotify:artist:4WN5naL3ofxrVBgFpguzKo"
        },
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/34v5MVKeQnIo0CWYMbbrPf"
          },
          "href": "https://api.spotify.com/v1/artists/34v5MVKeQnIo0CWYMbbrPf",
          "id": "34v5MVKeQnIo0CWYMbbrPf",
          "name": "John Newman",
          "type": "artist",
          "uri": "spotify:artist:34v5MVKeQnIo0CWYMbbrPf"
        }
      ],
      "disc_number": 1,
      "duration_ms": 219040,
      "explicit": false,
      "external_ids": {
        "isrc": "GBAHS1200163"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/5crHvEPQ13FbQGQSscm5Ns"
      },
      "href": "https://api.spotify.com/v1/tracks/5crHvEPQ13FbQGQSscm5Ns",
      "id": "5crHvEPQ13FbQGQSscm5Ns",
      "is_local": false,
      "is_playable": true,
      "name": "Feel the Love (feat. John Newman) - Radio Edit",
      "popularity": 45,
      "preview_url": "https://p.scdn.co/mp3-preview/6b07bf849ac8936d7b7f1a5b8215ab1a3b0749b2?cid=774b29d4f13844c495f206cafdad9c86",
      "track_number": 1,
      "type": "track",
      "uri": "spotify:track:5crHvEPQ13FbQGQSscm5Ns"
    },
    {
      "album": {
        "album_type": "ALBUM",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/1Dot4uMsJMx8n1Xi7gAdV6"
            },
            "href": "https://api.spotify.com/v1/artists/1Dot4uMsJMx8n1Xi7gAdV6",
            "id": "1Dot4uMsJMx8n1Xi7gAdV6",
            "name": "Jean-Yves Thibaudet",
            "type": "artist",
            "uri": "spotify:artist:1Dot4uMsJMx8n1Xi7gAdV6"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/0jJszR81GjA87jeRq0Jgwz"
            },
            "href": "https://api.spotify.com/v1/artists/0jJszR81GjA87jeRq0Jgwz",
            "id": "0jJszR81GjA87jeRq0Jgwz",
            "name": "Cleveland Orchestra",
            "type": "artist",
            "uri": "spotify:artist:0jJszR81GjA87jeRq0Jgwz"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/20iZXzMb8LoWXOeca32i82"
            },
            "href": "https://api.spotify.com/v1/artists/20iZXzMb8LoWXOeca32i82",
            "id": "20iZXzMb8LoWXOeca32i82",
            "name": "Vladimir Ashkenazy",
            "type": "artist",
            "uri": "spotify:artist:20iZXzMb8LoWXOeca32i82"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/23BiSNXm5UaRFuusoWisYO"
            },
            "href": "https://api.spotify.com/v1/artists/23BiSNXm5UaRFuusoWisYO",
            "id": "23BiSNXm5UaRFuusoWisYO",
            "name": "BBC Symphony Orchestra",
            "type": "artist",
            "uri": "spotify:artist:23BiSNXm5UaRFuusoWisYO"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/1sa3cLzMIDqNJgkNqHrhKt"
            },
            "href": "https://api.spotify.com/v1/artists/1sa3cLzMIDqNJgkNqHrhKt",
            "id": "1sa3cLzMIDqNJgkNqHrhKt",
            "name": "Hugh Wolff",
            "type": "artist",
            "uri": "spotify:artist:1sa3cLzMIDqNJgkNqHrhKt"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/6aXAOwRF0sBiDeQZwIo9zK"
        },
        "href": "https://api.spotify.com/v1/albums/6aXAOwRF0sBiDeQZwIo9zK",
        "id": "6aXAOwRF0sBiDeQZwIo9zK",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b273d5b0d64e972b9c2850a62f24",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e02d5b0d64e972b9c2850a62f24",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d00004851d5b0d64e972b9c2850a62f24",
            "width": 64
          }
        ],
        "name": "Warsaw Concerto - romantic piano classics from the silver screen",
        "release_date": "1998-01-01",
        "release_date_precision": "day",
        "total_tracks": 7,
        "type": "album",
        "uri": "spotify:album:6aXAOwRF0sBiDeQZwIo9zK"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/06LiIUiAEMBc6yLMXn2aEV"
          },
          "href": "https://api.spotify.com/v1/artists/06LiIUiAEMBc6yLMXn2aEV",
          "id": "06LiIUiAEMBc6yLMXn2aEV",
          "name": "Richard Addinsell",
          "type": "artist",
          "uri": "spotify:artist:06LiIUiAEMBc6yLMXn2aEV"
        },
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/1Dot4uMsJMx8n1Xi7gAdV6"
          },
          "href": "https://api.spotify.com/v1/artists/1Dot4uMsJMx8n1Xi7gAdV6",
          "id": "1Dot4uMsJMx8n1Xi7gAdV6",
          "name": "Jean-Yves Thibaudet",
          "type": "artist",
          "uri": "spotify:artist:1Dot4uMsJMx8n1Xi7gAdV6"
        },
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/23BiSNXm5UaRFuusoWisYO"
          },
          "href": "https://api.spotify.com/v1/artists/23BiSNXm5UaRFuusoWisYO",
          "id": "23BiSNXm5UaRFuusoWisYO",
          "name": "BBC Symphony Orchestra",
          "type": "artist",
          "uri": "spotify:artist:23BiSNXm5UaRFuusoWisYO"
        },
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/1sa3cLzMIDqNJgkNqHrhKt"
          },
          "href": "https://api.spotify.com/v1/artists/1sa3cLzMIDqNJgkNqHrhKt",
          "id": "1sa3cLzMIDqNJgkNqHrhKt",
          "name": "Hugh Wolff",
          "type": "artist",
          "uri": "spotify:artist:1sa3cLzMIDqNJgkNqHrhKt"
        }
      ],
      "disc_number": 1,
      "duration_ms": 540066,
      "explicit": false,
      "external_ids": {
        "isrc": "GBF079810080"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/1u8IzWRTBBznzdSs2SWJuS"
      },
      "href": "https://api.spotify.com/v1/tracks/1u8IzWRTBBznzdSs2SWJuS",
      "id": "1u8IzWRTBBznzdSs2SWJuS",
      "is_local": false,
      "is_playable": true,
      "linked_from": {
        "external_urls": {
          "spotify": "https://open.spotify.com/track/5pg9vSNAOFLtyZpUU42cBo"
        },
        "href": "https://api.spotify.com/v1/tracks/5pg9vSNAOFLtyZpUU42cBo",
        "id": "5pg9vSNAOFLtyZpUU42cBo",
        "type": "track",
        "uri": "spotify:track:5pg9vSNAOFLtyZpUU42cBo"
      },
      "name": "Warsaw Concerto",
      "popularity": 27,
      "preview_url": null,
      "track_number": 1,
      "type": "track",
      "uri": "spotify:track:1u8IzWRTBBznzdSs2SWJuS"
    },
    {
      "album": {
        "album_type": "ALBUM",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/7y97mc3bZRFXzT2szRM4L4"
            },
            "href": "https://api.spotify.com/v1/artists/7y97mc3bZRFXzT2szRM4L4",
            "id": "7y97mc3bZRFXzT2szRM4L4",
            "name": "Frédéric Chopin",
            "type": "artist",
            "uri": "spotify:artist:7y97mc3bZRFXzT2szRM4L4"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/0WBFyyZxQ5CeA31cKSmhU2"
            },
            "href": "https://api.spotify.com/v1/artists/0WBFyyZxQ5CeA31cKSmhU2",
            "id": "0WBFyyZxQ5CeA31cKSmhU2",
            "name": "Brigitte Engerer",
            "type": "artist",
            "uri": "spotify:artist:0WBFyyZxQ5CeA31cKSmhU2"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/2EJIGjaVFq9PKinjyA9yOn"
        },
        "href": "https://api.spotify.com/v1/albums/2EJIGjaVFq9PKinjyA9yOn",
        "id": "2EJIGjaVFq9PKinjyA9yOn",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b2731f07e718417b2e516d4b57bf",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e021f07e718417b2e516d4b57bf",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d000048511f07e718417b2e516d4b57bf",
            "width": 64
          }
        ],
        "name": "Chopin: Complete Nocturnes",
        "release_date": "2010-06-22",
        "release_date_precision": "day",
        "total_tracks": 21,
        "type": "album",
        "uri": "spotify:album:2EJIGjaVFq9PKinjyA9yOn"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/7y97mc3bZRFXzT2szRM4L4"
          },
          "href": "https://api.spotify.com/v1/artists/7y97mc3bZRFXzT2szRM4L4",
          "id": "7y97mc3bZRFXzT2szRM4L4",
          "name": "Frédéric Chopin",
          "type": "artist",
          "uri": "spotify:artist:7y97mc3bZRFXzT2szRM4L4"
        },
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/0WBFyyZxQ5CeA31cKSmhU2"
          },
          "href": "https://api.spotify.com/v1/artists/0WBFyyZxQ5CeA31cKSmhU2",
          "id": "0WBFyyZxQ5CeA31cKSmhU2",
          "name": "Brigitte Engerer",
          "type": "artist",
          "uri": "spotify:artist:0WBFyyZxQ5CeA31cKSmhU2"
        }
      ],
      "disc_number": 2,
      "duration_ms": 239973,
      "explicit": false,
      "external_ids": {
        "isrc": "FRZ149738100"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/0bcGY7mfG10QfeaDbz97hC"
      },
      "href": "https://api.spotify.com/v1/tracks/0bcGY7mfG10QfeaDbz97hC",
      "id": "0bcGY7mfG10QfeaDbz97hC",
      "is_local": false,
      "is_playable": true,
      "name": "Nocturne, Op. posth. in C-Sharp Minor: Lento",
      "popularity": 57,
      "preview_url": "https://p.scdn.co/mp3-preview/a3acd141b6add202307ae6b6f0dd843590435fe1?cid=774b29d4f13844c495f206cafdad9c86",
      "track_number": 10,
      "type": "track",
      "uri": "spotify:track:0bcGY7mfG10QfeaDbz97hC"
    },
    {
      "album": {
        "album_type": "SINGLE",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/1efrXlPhLKv7PvgUxVcqIS"
            },
            "href": "https://api.spotify.com/v1/artists/1efrXlPhLKv7PvgUxVcqIS",
            "id": "1efrXlPhLKv7PvgUxVcqIS",
            "name": "Emerson Drive",
            "type": "artist",
            "uri": "spotify:artist:1efrXlPhLKv7PvgUxVcqIS"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/5AnWd7MuTfFx4xJGvSdhRn"
        },
        "href": "https://api.spotify.com/v1/albums/5AnWd7MuTfFx4xJGvSdhRn",
        "id": "5AnWd7MuTfFx4xJGvSdhRn",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b273b03511c98033cd2f4c007b72",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e02b03511c98033cd2f4c007b72",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d00004851b03511c98033cd2f4c007b72",
            "width": 64
          }
        ],
        "name": "Just Got Paid",
        "release_date": "2017-03-17",
        "release_date_precision": "day",
        "total_tracks": 1,
        "type": "album",
        "uri": "spotify:album:5AnWd7MuTfFx4xJGvSdhRn"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/1efrXlPhLKv7PvgUxVcqIS"
          },
          "href": "https://api.spotify.com/v1/artists/1efrXlPhLKv7PvgUxVcqIS",
          "id": "1efrXlPhLKv7PvgUxVcqIS",
          "name": "Emerson Drive",
          "type": "artist",
          "uri": "spotify:artist:1efrXlPhLKv7PvgUxVcqIS"
        }
      ],
      "disc_number": 1,
      "duration_ms": 180685,
      "explicit": false,
      "external_ids": {
        "isrc": "CAUM81700064"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/60cLABum0U1SHPZ3dn0EpY"
      },
      "href": "https://api.spotify.com/v1/tracks/60cLABum0U1SHPZ3dn0EpY",
      "id": "60cLABum0U1SHPZ3dn0EpY",
      "is_local": false,
      "is_playable": true,
      "linked_from": {
        "external_urls": {
          "spotify": "https://open.spotify.com/track/41EYTKX66PslehSVrFdT4p"
        },
        "href": "https://api.spotify.com/v1/tracks/41EYTKX66PslehSVrFdT4p",
        "id": "41EYTKX66PslehSVrFdT4p",
        "type": "track",
        "uri": "spotify:track:41EYTKX66PslehSVrFdT4p"
      },
      "name": "Just Got Paid",
      "popularity": 40,
      "preview_url": "https://p.scdn.co/mp3-preview/d76045dc9fb567e5b93767f9280858e230db9bd8?cid=774b29d4f13844c495f206cafdad9c86",
      "track_number": 1,
      "type": "track",
      "uri": "spotify:track:60cLABum0U1SHPZ3dn0EpY"
    },
    {
      "album": {
        "album_type": "ALBUM",
        "artists": [
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/2kXJ68O899XvWOBdpzlXgs"
            },
            "href": "https://api.spotify.com/v1/artists/2kXJ68O899XvWOBdpzlXgs",
            "id": "2kXJ68O899XvWOBdpzlXgs",
            "name": "Nikolai Rimsky-Korsakov",
            "type": "artist",
            "uri": "spotify:artist:2kXJ68O899XvWOBdpzlXgs"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/3Nd3IdPZ8CDPAkwjGuz1MS"
            },
            "href": "https://api.spotify.com/v1/artists/3Nd3IdPZ8CDPAkwjGuz1MS",
            "id": "3Nd3IdPZ8CDPAkwjGuz1MS",
            "name": "Joseph Silverstein",
            "type": "artist",
            "uri": "spotify:artist:3Nd3IdPZ8CDPAkwjGuz1MS"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/0K23lQ2hSQAlxSEeZ05bjI"
            },
            "href": "https://api.spotify.com/v1/artists/0K23lQ2hSQAlxSEeZ05bjI",
            "id": "0K23lQ2hSQAlxSEeZ05bjI",
            "name": "Boston Symphony Orchestra",
            "type": "artist",
            "uri": "spotify:artist:0K23lQ2hSQAlxSEeZ05bjI"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/0atCvjK2GL6ezQFGOQOYQo"
            },
            "href": "https://api.spotify.com/v1/artists/0atCvjK2GL6ezQFGOQOYQo",
            "id": "0atCvjK2GL6ezQFGOQOYQo",
            "name": "Seiji Ozawa",
            "type": "artist",
            "uri": "spotify:artist:0atCvjK2GL6ezQFGOQOYQo"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/1XaPI6thQ3zTKqIU6sCvd2"
            },
            "href": "https://api.spotify.com/v1/artists/1XaPI6thQ3zTKqIU6sCvd2",
            "id": "1XaPI6thQ3zTKqIU6sCvd2",
            "name": "Gothenburg Symphony Orchestra",
            "type": "artist",
            "uri": "spotify:artist:1XaPI6thQ3zTKqIU6sCvd2"
          },
          {
            "external_urls": {
              "spotify": "https://open.spotify.com/artist/5UHZvYJA0aPcJSLYkYAeps"
            },
            "href": "https://api.spotify.com/v1/artists/5UHZvYJA0aPcJSLYkYAeps",
            "id": "5UHZvYJA0aPcJSLYkYAeps",
            "name": "Neeme Järvi",
            "type": "artist",
            "uri": "spotify:artist:5UHZvYJA0aPcJSLYkYAeps"
          }
        ],
        "external_urls": {
          "spotify": "https://open.spotify.com/album/3o4ng43mfCwXZ8h2HpTkYc"
        },
        "href": "https://api.spotify.com/v1/albums/3o4ng43mfCwXZ8h2HpTkYc",
        "id": "3o4ng43mfCwXZ8h2HpTkYc",
        "images": [
          {
            "height": 640,
            "url": "https://i.scdn.co/image/ab67616d0000b273c28f532b1c8e4288b253a636",
            "width": 640
          },
          {
            "height": 300,
            "url": "https://i.scdn.co/image/ab67616d00001e02c28f532b1c8e4288b253a636",
            "width": 300
          },
          {
            "height": 64,
            "url": "https://i.scdn.co/image/ab67616d00004851c28f532b1c8e4288b253a636",
            "width": 64
          }
        ],
        "name": "Rimsky-Korsakov: Scheherazade, Op. 35; Capriccio espagnol, Op. 34",
        "release_date": "2000-01-01",
        "release_date_precision": "day",
        "total_tracks": 9,
        "type": "album",
        "uri": "spotify:album:3o4ng43mfCwXZ8h2HpTkYc"
      },
      "artists": [
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/2kXJ68O899XvWOBdpzlXgs"
          },
          "href": "https://api.spotify.com/v1/artists/2kXJ68O899XvWOBdpzlXgs",
          "id": "2kXJ68O899XvWOBdpzlXgs",
          "name": "Nikolai Rimsky-Korsakov",
          "type": "artist",
          "uri": "spotify:artist:2kXJ68O899XvWOBdpzlXgs"
        },
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/1XaPI6thQ3zTKqIU6sCvd2"
          },
          "href": "https://api.spotify.com/v1/artists/1XaPI6thQ3zTKqIU6sCvd2",
          "id": "1XaPI6thQ3zTKqIU6sCvd2",
          "name": "Gothenburg Symphony Orchestra",
          "type": "artist",
          "uri": "spotify:artist:1XaPI6thQ3zTKqIU6sCvd2"
        },
        {
          "external_urls": {
            "spotify": "https://open.spotify.com/artist/5UHZvYJA0aPcJSLYkYAeps"
          },
          "href": "https://api.spotify.com/v1/artists/5UHZvYJA0aPcJSLYkYAeps",
          "id": "5UHZvYJA0aPcJSLYkYAeps",
          "name": "Neeme Järvi",
          "type": "artist",
          "uri": "spotify:artist:5UHZvYJA0aPcJSLYkYAeps"
        }
      ],
      "disc_number": 1,
      "duration_ms": 306146,
      "explicit": false,
      "external_ids": {
        "isrc": "DEF058702922"
      },
      "external_urls": {
        "spotify": "https://open.spotify.com/track/6KMYMRtdJl6lrubE7MbVMN"
      },
      "href": "https://api.spotify.com/v1/tracks/6KMYMRtdJl6lrubE7MbVMN",
      "id": "6KMYMRtdJl6lrubE7MbVMN",
      "is_local": false,
      "is_playable": true,
      "name": "Capriccio Espagnol, Op.34: 2. Variazioni",
      "popularity": 14,
      "preview_url": null,
      "track_number": 6,
      "type": "track",
      "uri": "spotify:track:6KMYMRtdJl6lrubE7MbVMN"
    }
  ],
  "seeds": [
    {
      "initialPoolSize": 257,
      "afterFilteringSize": 257,
      "afterRelinkingSize": 257,
      "id": "4NHQUGzhtTLFvgF5SZesLK",
      "type": "ARTIST",
      "href": "https://api.spotify.com/v1/artists/4NHQUGzhtTLFvgF5SZesLK"
    },
    {
      "initialPoolSize": 307,
      "afterFilteringSize": 307,
      "afterRelinkingSize": 307,
      "id": "0c6xIDDpzE81m2q797ordA",
      "type": "TRACK",
      "href": "https://api.spotify.com/v1/tracks/0c6xIDDpzE81m2q797ordA"
    },
    {
      "initialPoolSize": 402,
      "afterFilteringSize": 402,
      "afterRelinkingSize": 402,
      "id": "classical",
      "type": "GENRE",
      "href": null
    },
    {
      "initialPoolSize": 390,
      "afterFilteringSize": 390,
      "afterRelinkingSize": 390,
      "id": "country",
      "type": "GENRE",
      "href": null
    }
  ]
}
```

## Components
##### Writing out your components and its descriptions isn't a required part of the proposal but can be helpful.

Based on the initial logic defined in the previous sections try and breakdown the logic further into stateless/stateful components. 

| Component | Description | 
| --- | :---: |  
| App | This will make the initial data pull and include React Router| 
| Header | This will render the header include the nav | 
| Footer | This will render the header include the nav | 


## Additional Libraries
 Use this section to list all supporting libraries and thier role in the project such as Axios, ReactStrap, D3, etc. 

## Code Snippet

Use this section to include a brief code snippet of functionality that you are proud of an a brief description.  Code snippet should not be greater than 10 lines of code. 

```
function reverse(string) {
	// here is the code to reverse a string of text
}
```
