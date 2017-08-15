# URL SHORTNER

A HTTP-based RESTful API for generating and managing Short URLs and redirectiong clients.

## API Description
### Shorten Url
  Returns json data with shortened url.
* **URL**
  /api/shorten
* **Method:**
  `POST`
*  **Data Params**

   **Required:**
    `url=some Long url`
* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"shortenedURL":"http://localhost:4000/r1JOuhlu-"}`
 
* **Sample Call:**
  See Curl section below
  
### Use Short Url

### Request Stats


## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites



```
Node
MongoDB
```

### Installing

1 - Install MongoDb
```
brew update
brew install mongodb
```
2 - Fork and clone repo
```
git clone https://github.com/AWattNY/shortlyCF.git
```
3 - install package
```
$ npm install 
```
3 - Run
```
$ node app.js
```

## Running the tests

Open a seperate tab and run 
```
$ npm test
```
## Testing API using curl

Create Short Url
```
$ curl -i -d "url=www.google.com" http://localhost:4000/api/shorten
```
Server will reply with the following JSON Object
```
{"shortenedURL":"http://localhost:4000/r1JOuhlu-"}
```
Trying the same long url twice returns a different short url
```
$ curl -i -d "url=www.google.com" http://localhost:4000/api/shorten
```
Server will reply with a different short url
```
{"shortenedURL":"http://localhost:4000/SkzUYhgOW"}
```
To use a Short Url
```
$ curl http://localhost:4000/SkzUYhgOW
```
Server reply should be 
```
Found. Redirecting to http://www.google.com
```
For testing purpusoes this get request also accepts a testDate query parameter
for example to simulate short url use an hour later
```
curl http://localhost:4000/SkzUYhgOW?testDate=2017-08-15T19:15:46.778Z
```
Requesting short url Access Stats from API:
Last 24 hours
```
$ curl http://localhost:4000/stats/SkzUYhgOW/last24
```
Past Week
```
$ curl http://localhost:4000/stats/SkzUYhgOW/pastWeek
```
All Time
```
$ curl http://localhost:4000/stats/SkzUYhgOW/allTime
```
For testing purpusoes the stats route also accepts a testDate query parameter
```
$ curl http://localhost:4000/stats/SkzUYhgOW/last24?testDate=2017-08-17T18:00:02.534Z
```

## Built With
[ExpressJS](https://expressjs.com/)<br />
[Shortid](https://www.npmjs.com/package/supertest)<br />
[MochaJS](https://mochajs.org/)<br />
[Supertest](https://www.npmjs.com/package/supertest)


## Author
Adam Watt

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details


