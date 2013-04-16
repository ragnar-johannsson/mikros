## Mikros

A URL shortener for Nginx/OpenResty with a Redis backend.


### Setup

1. Install OpenResty & setup a Redis instance to use
2. Adjust the nginx.conf file, particularly the four variables at the start of the server section 
3. Fire up nginx with the config file


### Usage

Get a shortened URL by posting it to `/`, in a JSON object:

```
$ curl -X POST --data '{"url":"http://google.com"}' http://localhost:1234
{"originalurl":"http://google.com","shorturl":"http://my.host:1234/c7b920f57e"}
$
```
A json object with entries `original_url` and `short_url` is returned.


### Notes

The code has no collision detection of hashes. It uses a 40bit truncated MD5 sum for a hash; if a collision occurs the key is overwritten with the new value.


### License

Simplified BSD. See the LICENSE file for details.
