# Check 1

![photo](images/check1.png)

# Check 2

![photo](images/check2.png)
![photo](images/check2_movies.png)

# Check 3

![photo](images/check3.png)


# Check 4

Movies after 1987: 

{"docs":[
{"_id":"00a271787f89c0ef2e10e88a0c0001f4","_rev":"1-c7f3ec5e61c7a461d83da2d42f64a9e4","type":"movie","title":"My Neighbour Totoro","year":1988,"director":"miyazaki","rating":8.2},
{"_id":"00a271787f89c0ef2e10e88a0c0003f0","_rev":"1-5facb9c84b721a5fe8d667c1140a54d3","type":"movie","title":"Kikis Delivery Service","year":1989,"director":"miyazaki","rating":7.8},
{"_id":"00a271787f89c0ef2e10e88a0c00048b","_rev":"1-90be3f3651b72d82da71a875e63de9c0","type":"movie","title":"Princess Mononoke","year":1997,"director":"miyazaki","rating":8.4}
],
"bookmark": "g2wAAAACaAJkAA5zdGFydGtleV9kb2NpZG0AAAAgMDBhMjcxNzg3Zjg5YzBlZjJlMTBlODhhMGMwMDA0OGJoAmQACHN0YXJ0a2V5bAAAAAFiAAAHzWpq"}


Movies after "L" without indexing: 

{"docs":[
{"_id":"00a271787f89c0ef2e10e88a0c0001f4","_rev":"1-c7f3ec5e61c7a461d83da2d42f64a9e4","type":"movie","title":"My Neighbour Totoro","year":1988,"director":"miyazaki","rating":8.2},
{"_id":"00a271787f89c0ef2e10e88a0c00048b","_rev":"1-90be3f3651b72d82da71a875e63de9c0","type":"movie","title":"Princess Mononoke","year":1997,"director":"miyazaki","rating":8.4}
],
"bookmark": "g1AAAABweJzLYWBgYMpgSmHgKy5JLCrJTq2MT8lPzkzJBYorGBgkGpkbmluYp1lYJhukphmlGhqkWlgkGiQbGBiYWCSB9HHA9BGlIwsAfPcdnw",
"warning": "No matching index found, create an index to optimize query time."}



Indexing Command: 

curl -X POST admin:adminpass@localhost:5984/hello-world/_index -d '{
   "index": {
      "fields": [
         "title"
      ]
   },
   "name": "title-json-index",
   "type": "json"
}' -H 'Content-Type: application/json'

Movie Query: 

curl -X POST admin:adminpass@localhost:5984/hello-world/_find -d '{
   "selector": {
      "title": {
         "$gt": "l"
    }
  }
}' -H 'Content-Type: application/json'
