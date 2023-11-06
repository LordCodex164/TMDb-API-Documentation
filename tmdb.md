# The Movie Database (TMDb) API Documentation

## Introduction

The Movie Database (TMDb) API is the api where you can find definitive lists of currently available methods for movie, tv, actor and image APIs. It is also a popular and a user editable database for Movie Shows. The Purpose of the API is to create endpoints for developers who are looking to integrate Movie, tv and image APIs into their Applications.

## Getting Started

### Get started with the basics of the TMDB API.

Before using the API, ensure you have your api key to test the (TMDb) API. If you don’t have one yet, you can create it [here](https://www.themoviedb.org/settings/api) from your account setting page.

Please be well informed that the registration process is not well optimized on mobile devices and only be done on a Laptop or Desktop.

Once you have been given an API key, follow this use case for an API Key based request

```
curl --request GET \
     --url 'https://api.themoviedb.org/3/movie/11?api_key=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
```

In this case after having your api key based request, you can go on [postman](https://www.postman.com) to test it and inspect how your data should look like: 

```js
{
"adult": false,
"backdrop_path": "/4qCqAdHcNKeAHcK8tJ8wNJZa9cx.jpg",
"belongs_to_collection": {
"id": 10,
"name": "Star Wars Collection",
"poster_path": "/gq5Wi7i4SF3lo4HHkJasDV95xI9.jpg",
"backdrop_path": "/d8duYyyC9J5T825Hg7grmaabfxQ.jpg"
},
"budget": 11000000,
"genres": [
{
"id": 12,
"name": "Adventure"
},
{
"id": 28,
"name": "Action"
},
{
"id": 878,
"name": "Science Fiction"
}
],
"homepage": "http://www.starwars.com/films/star-wars-episode-iv-a-new-hope",
"id": 11,
"imdb_id": "tt0076759",
"original_language": "en",
"original_title": "Star Wars",
"overview": "Princess Leia is captured and held hostage by the evil Imperial forces in their effort to take over the galactic Empire. Venturesome Luke Skywalker and dashing captain Han Solo team together with the loveable robot duo R2-D2 and C-3PO to rescue the beautiful princess and restore peace and justice in the Empire.",
"popularity": 95.381,
"poster_path": "/6FfCtAuVAW8XJjZ7eWeLibRLWTw.jpg",
"production_companies": [
{
"id": 1,
"logo_path": "/o86DbpburjxrqAzEDhXZcyE8pDb.png",
"name": "Lucasfilm Ltd.",
"origin_country": "US"
},
{
"id": 25,
"logo_path": "/qZCc1lty5FzX30aOCVRBLzaVmcp.png",
"name": "20th Century Fox",
"origin_country": "US"
}


],
"production_countries": [
{
"iso_3166_1": "US",
"name": "United States of America"
}
],
"release_date": "1977-05-25",
"revenue": 775398007,
"runtime": 121,
"spoken_languages": [
{
"english_name": "English",
"iso_639_1": "en",
"name": "English"
}
],
"status": "Released",
"tagline": "A long time ago in a galaxy far, far away...",
"title": "Star Wars",
"video": false,
"vote_average": 8.204,
"vote_count": 19261
}

```

> Before proceeding further, it is highly recommended you use postman to test the endpoints.

## Authenticating Requests

### Application Level Authentication

There is a term which is basically used to authenticate a user when sending requests. When sending requests to an api endpoint, there is a need to authenticate those requests and it is only possible with a token. In this case, we will be using our access token as a Bearer token to authenticate our requests. To get the access token, head into your account page, under the API settings section, you will see a new token listed called API Read Access Token. This token is expected to be sent along as an Authorization header. A simple cURL example using this method looks like the following

curl --request GET \
     --url 'https://api.themoviedb.org/3/movie/11' \
     --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJhZGYxZjgyN2VmMTVhYWE2ZjVlZDIxOTk0ZmVmNzZkYyIsInN1YiI6IjY1NDNjNGU5NzcxOWQ3MDExYzkyOTJhMyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.SdGVUI7GLQPfIYcJmLiFWxmgjVccJQiL8DWQ198yhCs'

When you have the access token, a single authentication process is performed throughout the application.

## Testing Endpoints

In the previous section, you looked at application level authentication and how it works using the (TMDB) Api. In this section, you will be exploring different key endpoints.

### Getting Account Details 

**API KEY** : adf1f827ef15aaa6f5ed21994fef76dc

**HTTP METHOD** : GET Request. 

**EndPoint Url** : https://api.themoviedb.org/3/account/{account_id}

**Feature** : With a request to this endpoint, we get our (TMDB) account details.

The account id is the id for your (TMDB) account. In this case the id for the account is 20656973

**Request Headers** : Inside the Headers, make sure you pass in your access token which helps authenticate the request which should look like the following:  👇

eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJhZGYxZjgyN2VmMTVhYWE2ZjVlZDIxOTk0ZmVmNzZkYyIsInN1YiI6IjY1NDNjNGU5NzcxOWQ3MDExYzkyOTJhMyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.SdGVUI7GLQPfIYcJmLiFWxmgjVccJQiL8DWQ198yhCs'

**Response Status Code** : [200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200#:~:text=The%20HTTP%20200%20OK%20success,that%20the%20request%20has%20succeeded)

**Response JSON format** :

Here is how the data should look like in JSON format:

```js
{
"avatar": {
"gravatar": {
"hash": "52258d9c8b7a44b216917c5eef69f8c0"
},
"tmdb": {
"avatar_path": null
}
},
"id": 20656973,
"iso_639_1": "en",
"iso_3166_1": "NG",
"name": "",
"include_adult": false,
"username": "LordCodex"
}
```



### Movie List Endpoint

**API KEY** : adf1f827ef15aaa6f5ed21994fef76dc

**HTTP METHOD** : GET

**Endpoint URL** : https://api.themoviedb.org/3/movie/changes

**Request Headers** : In the request headers, pass in your access token that helps in authenticating your request 👇

eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJhZGYxZjgyN2VmMTVhYWE2ZjVlZDIxOTk0ZmVmNzZkYyIsInN1YiI6IjY1NDNjNGU5NzcxOWQ3MDExYzkyOTJhMyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.SdGVUI7GLQPfIYcJmLiFWxmgjVccJQiL8DWQ198yhCs

**Feature** : Get a list of all of the movie ids that have been changed in the past 24 hours.

**Response Status Code** : [200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200#:~:text=The%20HTTP%20200%20OK%20success,that%20the%20request%20has%20succeeded).

**Response JSON format**:

Here is how the data should look like in JSON format:

```js
{
    "results": [
        {
            "id": 15708,
            "adult": false
        },
        {
            "id": 1200897,
            "adult": false
        },
        {
            "id": 1200882,
            "adult": false
        },
        {
            "id": 643236,
            "adult": false
        },
    ]
}

```
### Languages

**API KEY** : adf1f827ef15aaa6f5ed21994fef76dc

**HTTP Method** : GET

**Endpoint URL** : https://api.themoviedb.org/3/configuration/languages

**Feature** : Get the list of languages (ISO 639-1 tags) used throughout TMDB.

**Request Headers** : In the request headers, pass in your access token that helps in authenticating your request 👇

eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJhZGYxZjgyN2VmMTVhYWE2ZjVlZDIxOTk0ZmVmNzZkYyIsInN1YiI6IjY1NDNjNGU5NzcxOWQ3MDExYzkyOTJhMyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.SdGVUI7GLQPfIYcJmLiFWxmgjVccJQiL8DWQ198yhCs


**Response Status Code** : [200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200#:~:text=The%20HTTP%20200%20OK%20success,that%20the%20request%20has%20succeeded).


**Response JSON format**:

```js
[
    {
        "iso_639_1": "xx",
        "english_name": "No Language",
        "name": "No Language"
    },
    {
        "iso_639_1": "aa",
        "english_name": "Afar",
        "name": ""
    },
    {
        "iso_639_1": "af",
        "english_name": "Afrikaans",
        "name": "Afrikaans"
    },
    {
        "iso_639_1": "ak",
        "english_name": "Akan",
        "name": ""
    },
    {
        "iso_639_1": "an",
        "english_name": "Aragonese",
        "name": ""
    },
]
```


### Jobs

**API KEY** : adf1f827ef15aaa6f5ed21994fef76dc

**HTTP Method** : GET

**Endpoint URL** : https://api.themoviedb.org/3/configuration/jobs

**Feature** : Get the list of the jobs and departments we use on TMDB.

**Response Status Code** : [200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200#:~:text=The%20HTTP%20200%20OK%20success,that%20the%20request%20has%20succeeded).

** Response JSON format: 

```js
[
    {
        "department": "Directing",
        "jobs": [
            "Director",
            "Script Supervisor",
            "Layout",
            "Continuity",
            "Special Guest Director",
            "Other",
            "Assistant Director",
            "Co-Director",
            "Second Assistant Director",
            "Third Assistant Director",
            "Script Coordinator",
            "First Assistant Director",
            "Insert Unit Director",
            "Second Second Assistant Director",
            "Second Unit First Assistant Director",
            "Insert Unit First Assistant Director",
            "Field Director",
            "Crowd Assistant Director",
            "Stage Director",
            "Action Director",
            "Additional Second Assistant Director",
            "Assistant Director Trainee",
            "Second Assistant Director Trainee",
            "Additional Third Assistant Director",
            "First Assistant Director (Prep)",
            "First Assistant Director Trainee",
            "Second Unit Director",
            "Series Director"
        ]
    },
    {
        "department": "Sound",
        "jobs": [
            "Music Editor",
            "Sound Designer",
            "Sound Recordist",
            "Assistant Sound Editor",
            "Sound Effects",
            "Supervising ADR Editor",
            "Utility Sound",
            "Original Music Composer",
            "Music Supervisor",
            "ADR Supervisor",
            "Playback Singer",
            "Supervising Music Editor",
            "Sound Director",
            "Dialogue Editor",
            "Boom Operator",
            "Songs",
            "Orchestrator",
            "Supervising Sound Effects Editor",
            "Recording Supervision",
            "Additional Music Supervisor",
            "Sound",
            "Musician",
            "Music Programmer",
            "Scoring Mixer",
            "Additional Sound Re-Recordist",
            "Supervising Sound Editor",
            "Sound Re-Recording Mixer",
            "Sound Engineer",
            "Foley Editor",
            "Music Score Producer",
            "Additional Soundtrack",
            "Foley",
            "Sound Montage Associate",
            "Music Director",
            "Sound Effects Editor",
            "Music",
            "First Assistant Sound Editor",
            "Dolby Consultant",
            "Production Sound Mixer",
            "Other",
            "Sound Effects Designer",
            "Theme Song Performance",
            "ADR & Dubbing",
            "Vocal Coach",
            "Additional Sound Re-Recording Mixer",
            "Assistant Music Supervisor",
            "Supervising Dialogue Editor",
            "Sound Editor",
            "Sound Mixer",
            "ADR Editor",
            "Apprentice Sound Editor",
            "Conductor",
            "Foley Recordist",
            "Assistant Dialogue Editor",
            "Assistant Sound Designer",
            "Foley Recording Engineer",
            "Music Sound Design and Processing",
            "Second Assistant Sound",
            "Music Coordinator",
            "O.B. Sound",
            "ADR Engineer",
            "Audio Post Coordinator",
            "Location Sound Recordist",
            "Music Consultant",
            "Sound Technical Supervisor",
            "Assistant Sound Engineer",
            "Sound Mix Technician",
            "Additional Production Sound Mixer",
            "Foley Mixer",
            "Keyboard Programmer",
            "Location Sound Assistant",
            "Sound Post Production Coordinator",
            "ADR Recordist",
            "Loop Group Coordinator",
            "Music Producer",
            "ADR Recording Engineer",
            "Sound Supervisor",
            "ADR Editor",
            "Foley Artist",
            "Joint ADR Mixer",
            "Sound Assistant",
            "Sound Post Supervisor",
            "Assistant Foley Artist",
            "Music Arranger",
            "Music Supervision Assistant",
            "ADR Coordinator",
            "Main Title Theme Composer",
            "Music Co-Supervisor",
            "ADR Post Producer",
            "Foley Supervisor",
            "Sound Re-Recording Assistant",
            "ADR Mixer",
            "Digital Foley Artist",
            "Location Sound Mixer",
            "Vocals"
        ]
    },
    {
        "department": "Visual Effects",
        "jobs": [
            "Chief Technician / Stop-Motion Expert",
            "Visual Development",
            "Animation Manager",
            "I/O Manager",
            "3D Modeller",
            "CGI Director",
            "Mechanical Designer",
            "Animation Fix Coordinator",
            "Pyrotechnic Supervisor",
            "Animation Director",
            "Battle Motion Coordinator",
            "Visual Effects Producer",
            "Color Designer",
            "Pre-Visualization Supervisor",
            "3D Animator",
            "Fix Animator",
            "VFX Supervisor",
            "Character Modelling Supervisor",
            "Visual Effects Technical Director",
            "Visual Effects",
            "Animation Supervisor",
            "Simulation & Effects Artist",
            "3D Supervisor",
            "Creature Technical Director",
            "Lead Character Designer",
            "VFX Director of Photography",
            "Imaging Science",
            "VFX Editor",
            "2D Artist",
            "3D Coordinator",
            "3D Tracking Layout",
            "Creature Design",
            "Visual Effects Supervisor",
            "Visual Effects Designer",
            "Digital Compositor",
            "Matchmove Supervisor",
            "Stereoscopic Coordinator",
            "VFX Lighting Artist",
            "Shading",
            "VFX Production Coordinator",
            "Simulation & Effects Production Assistant",
            "Key Animation",
            "Lead Animator",
            "Opening/Ending Animation",
            "I/O Supervisor",
            "Special Effects Supervisor",
            "2D Supervisor",
            "Character Designer",
            "Animation Department Coordinator",
            "3D Director",
            "3D Sequence Supervisor",
            "CG Animator",
            "CG Painter",
            "VFX Artist",
            "3D Artist",
            "Animation Production Assistant",
            "Mechanical & Creature Designer",
            "Cloth Setup",
            "CG Engineer",
            "Additional Effects Development",
            "Visual Effects Coordinator",
            "3D Generalist",
            "Digital Effects Producer",
            "Roto Supervisor",
            "Animation",
            "Modeling",
            "24 Frame Playback",
            "Creature Effects Technical Director",
            "Visual Effects Assistant Editor",
            "Visual Effects Director",
            "Visual Effects Production Manager",
            "Cyber Scanning Supervisor",
            "Generalist",
            "Visual Effects Camera",
            "Compositing Artist",
            "Compositing Supervisor",
            "Rotoscoping Artist",
            "Senior Modeller",
            "Stereoscopic Technical Director",
            "Director of Previsualization",
            "Photo Retouching",
            "Smoke Artist",
            "CG Artist",
            "Digital Film Recording",
            "Head of Animation",
            "Senior Animator",
            "Visual Effects Compositor",
            "Animation Coordinator",
            "Layout Supervisor",
            "Pre-Visualization Coordinator",
            "Visual Effects Production Assistant",
            "Modelling Supervisor",
            "Senior Visual Effects Supervisor",
            "Animation Technical Director",
            "2D Sequence Supervisor",
            "Lead Creature Designer",
            "Visual Effects Lineup",
            "Senior Generalist",
            "Compositing Lead",
            "Matte Painter",
            "Pipeline Technical Director",
            "Supervising Animation Director",
            "Additional Visual Effects",
            "Effects Supervisor",
            "Stereoscopic Supervisor"
        ]
    },
   
]



```

## Now Playing

**HTTP METHOD** : GET

**Endpoint Url** : https://api.themoviedb.org/3/movie/now_playing

**Feature** : Get a list of movies that are currently in theatres.

**Response Status Code** : [200](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200#:~:text=The%20HTTP%20200%20OK%20success,that%20the%20request%20has%20succeeded).

**Response JSON format** : 

``` js
{
    "dates": {
        "maximum": "2023-11-08",
        "minimum": "2023-09-27"
    },
    "page": 1,
    "results": [
        {
            "adult": false,
            "backdrop_path": "/eSsMzJpzAwCa69tm6Wco2il44aJ.jpg",
            "genre_ids": [
                28,
                80,
                18,
                53
            ],
            "id": 939335,
            "original_language": "en",
            "original_title": "Muzzle",
            "overview": "LAPD K-9 officer Jake Rosser has just witnessed the shocking murder of his dedicated partner by a mysterious assailant. As he investigates the shooter’s identity, he uncovers a vast conspiracy that has a chokehold on the city in this thrilling journey through the tangled streets of Los Angeles and the corrupt bureaucracy of the LAPD.",
            "popularity": 1864.674,
            "poster_path": "/qXChf7MFL36BgoLkiB3BzXiwW82.jpg",
            "release_date": "2023-09-29",
            "title": "Muzzle",
            "video": false,
            "vote_average": 6.175,
            "vote_count": 83
        },
        {
            "adult": false,
            "backdrop_path": "/askg3SMvhqEl4OL52YuvdtY40Yb.jpg",
            "genre_ids": [
                10751,
                16,
                14,
                10402,
                35,
                12
            ],
            "id": 354912,
            "original_language": "en",
            "original_title": "Coco",
            "overview": "Despite his family’s baffling generations-old ban on music, Miguel dreams of becoming an accomplished musician like his idol, Ernesto de la Cruz. Desperate to prove his talent, Miguel finds himself in the stunning and colorful Land of the Dead following a mysterious chain of events. Along the way, he meets charming trickster Hector, and together, they set off on an extraordinary journey to unlock the real story behind Miguel's family history.",
            "popularity": 1208.387,
            "poster_path": "/gGEsBPAijhVUFoiNpgZXqRVWJt2.jpg",
            "release_date": "2017-10-27",
            "title": "Coco",
            "video": false,
            "vote_average": 8.217,
            "vote_count": 18061
        },
        {
            "adult": false,
            "backdrop_path": "/zgQQF04u3OgNBJqClRNby1FPz9s.jpg",
            "genre_ids": [
                16,
                10751,
                28,
                878
            ],
            "id": 893723,
            "original_language": "en",
            "original_title": "PAW Patrol: The Mighty Movie",
            "overview": "A magical meteor crash lands in Adventure City and gives the PAW Patrol pups superpowers, transforming them into The Mighty Pups.",
            "popularity": 1129.57,
            "poster_path": "/aTvePCU7exLepwg5hWySjwxojQK.jpg",
            "release_date": "2023-09-21",
            "title": "PAW Patrol: The Mighty Movie",
            "video": false,
            "vote_average": 6.932,
            "vote_count": 118
        },
        {
            "adult": false,
            "backdrop_path": "/pA3vdhadJPxF5GA1uo8OPTiNQDT.jpg",
            "genre_ids": [
                28,
                18
            ],
            "id": 678512,
            "original_language": "en",
            "original_title": "Sound of Freedom",
            "overview": "The story of Tim Ballard, a former US government agent, who quits his job in order to devote his life to rescuing children from global sex traffickers.",
            "popularity": 1056.898,
            "poster_path": "/qA5kPYZA7FkVvqcEfJRoOy4kpHg.jpg",
            "release_date": "2023-07-03",
            "title": "Sound of Freedom",
            "video": false,
            "vote_average": 8.136,
            "vote_count": 1171
        },
        {
            "adult": false,
            "backdrop_path": "/tj7mp7uWjVw5N73G5Hwm1bkMOcD.jpg",
            "genre_ids": [
                28,
                10752
            ],
            "id": 975902,
            "original_language": "en",
            "original_title": "Boudica",
            "overview": "Inspired by events in A.D. 60, Boudica follows the eponymous Celtic warrior who rules the Iceni people alongside her husband Prasutagus. When he dies at the hands of Roman soldiers, Boudica’s kingdom is left without a male heir and the Romans seize her land and property.  Driven to the edge of madness and determined to avenge her husband’s death, Boudica rallies the various tribes from the region and wages an epic war against the mighty Roman empire.",
            "popularity": 857.214,
            "poster_path": "/ssEFC5wfFjj7lJpUgwJDOK1Xu1J.jpg",
            "release_date": "2023-10-26",
            "title": "Boudica",
            "video": false,
            "vote_average": 6.625,
            "vote_count": 12
        },
    ],
    "total_pages": 103,
    "total_results": 2059
}

```

## Rate Limiting

It is a technique or method that restricts the amount of requests made to a server or service so as to reduce traffic flow. According to [TMDb](https://developer.themoviedb.org/docs/rate-limiting) as of December 16th, 2019, 
the original rate limiting (40 seconds per second) was disabled. However, upper limits are still put in place to ensure that excessive bulk scraping is mitigated and reduced.

## Usage Guidelines

In the previous section, you covered the term rate limiting and why it is used in an api. Now, let's delve into best practices for using the TMDb API effectively and responsibly.

1. Ensure to set up Postman for API testing. If you still don’t know how, click [here](https://www.youtube.com/watch?v=h0CZ5V5kzEo).

2. Read and review the [(TMDB) Official documentation](https://developer.themoviedb.org/docs/getting-started) yourself to understand how the API works.

3. API key: Sign up for a TMDb API key by visiting [TMDb API](https://www.themoviedb.org/documentation/api).

4. Access Token: Head into your account page, under the API settings section, you will see a new token listed called API Read Access Token which you will pass as your authorization header.

5. Test Endpoints: Check the TMDb endpoints and start testing on Postman to have access to their data.

6. Respect Rate Limits: Rate Limits are now disabled. However, there are still higher limits that are imposed by TMDb.

## Testing Methods

In this section, I will suggest two(2) methods that you can use to test the TMDb API effectively.

**Manual Testing** : With this method, APIs are tested manually by sending HTTP requests using tools like Postman. You can primarily interact with the postman user interface 
as a manual tool to test APIs and inspect responses.


**Automated Testing** : This method involves using specialized software tools to automate a human driven manual process. An automating tool is required in this method in writing test cases. 
Examples of automated testing tools include Newman which is a command line collection runner for postman. Newman allows you to run postman collection directly from the command line.






