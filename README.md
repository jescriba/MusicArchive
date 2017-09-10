# Music Archive

w.i.p

### Motivation

You are a "band manager" who wants to create an archive of music for artists you manage. You act as the admin for all this content. You want to be able to associate a song with a collection of artists that you can then share and search through. This is a flat hierarchy structure - as in the band manager creates the songs and associations for _any_ artist. **Then** this project is for you!

 Detailed in the Setup section is how to quickly get a web backend/frontend and iOS client up and running with minimal steps. This assumes minimal technical ability and ideally minimal debugging/configuration time.
 
 For further info, check out the API/Schema section.

### Set Up

**Assumptions** 

This is the tech stack you are inheriting with this project. I'm sure you could swap it out if you wanted to spend more time with configuring, but I'm hoping this stack sets you up for success most _easily_ and _quickly_.

- Heroku [Home](https://www.heroku.com/) - for deploying web app
- AWS S3 [Home](https://aws.amazon.com/s3/) - song cloud storage
- Redis [Home](https://redis.io/) - Used for queuing transcoding jobs for handling lossless -> lossy audio conversion (both versions will be stored and downloadable from the client) using redis-to-go heroku plugin
- Ruby on Rails (for Web/Backend) - technology behind web app - ideally you won't manage this much outside of cloning the web submodule
- Swift/Xcode (for iOS) - technology behind the iPhone app - ideally you won't manage this much outside of cloning the iOS submodule

you can host this for _cheap_. Free heroku web app + a few cents a month on S3 (assuming modest storage/access).

**Instructions**

TODO Detailed deployment/setup instructions w/ pics/videos

TODO Add deploy to heroku

https://devcenter.heroku.com/articles/heroku-button
https://devcenter.heroku.com/articles/app-json-schema

## Web

Web frontend and backend for setting up Music Archive API

[Source](http://www.github.com/jescriba/MusicArchive-Web)

### API/Schema

If you follow the instructions, you'll be set up with this API to connect to via the web or iOS clients. **Note:** These endpoints will return html or json (based on the http request `Accept` header) making adding additional clients or customization a breeze!

These are the endpoints and model schema set up for you:

**Artists**

Ex:

```
{
    "id": 10,
    "name": "jdawg",
    "description": null,
    "url": null,
    "private": false,
    "created_at": "2017-07-13T21:36:18+00:00"
  }
```

API endpoints:

```
/artists     # List Artists
/artists/:id # Get Artist Info By Id
```

**Albums**

TODO

API endpoints:

```
/albums
```

**Songs**

Ex:

```
{
    "id": 408,
    "name": "chopin grand waltz in a minor",
    "description": null,
    "url": "https://amazon-aws.com/bucket/music/primary-artist/07-16-2017.mp3",
    "lossless_url": "https://amazon-aws.com/bucket/music/primary-artist/07-16-2017.aif",
    "private": false,
    "created_at": "2017-07-17T16:32:41+00:00",
    "recorded_at": "2017-07-16T00:00:00+00:00",
    "liked": false,
    "likes": 0,
    "artists": [
      {
        "id": 1,
        "name": "jdwag",
        "description": null,
        "url": null,
        "private": false,
        "created_at": "2016-10-17T06:16:48+00:00"
      }
    ]
  }
```

API endpoints:

```
/songs     # List Songs
/songs/:id # Get Song Info By Id
```

**Associations**

_Artist_ has many _Songs_

Additional endpoint: 

```
/artists/:id/songs # List Artist :id 's Songs
```

_Artist_ has many _Albums_

_Song_ has many _Artists_

**Search**

API endpoints:

```
```

### Demo
TODO include video demo

## iOS

Mobile client for accessing data from the Music Archive API you set up. You can easily "tap into" your base end point i.e. `www.my-awesome-achive.com` then connect instantly to your data.

Written in Swift, you can easily change important configuration settings in `Constants.swift` and UI in the Storyboard.

[Source](http://www.github.com/jescriba/MusicArchive-iOS)

### Demo
TODO include video demo