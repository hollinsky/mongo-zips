mongo-zips
==========

This is a list of all US zip codes and their corresponding latitude, longitude, cities, and states, formatted in such a way that allows them to be imported into MongoDB. Credit to The Zip Code Database Project for the data.

To use this, you'll basically want to create yourself a collection for the data you'll be putting in, and then copy-paste the whole zips.json file into an insert command on that collection.

I'm no MongoDB master, so there may be an easier way to do this.

The zip code data itself is not mine, nor do I have any way to keep it up to date. It's simply the data that was already available at The Zip Code Database formatted so that it imports into your database. If you find a problem with it, you can open an issue or submit a pull request and I can take a look.

Here I've also included a distance function for Javascript, which takes two latitude and longitdue pairs and returns the distance between them in miles.

```javascript
function distance(lat1, lon1, lat2, lon2)
{
    var calculation = (Math.sin(lat1 * (Math.PI / 180)) *
                       Math.sin(lat2 * (Math.PI / 180)) +
                       Math.cos(lat1 * (Math.PI / 180)) *
                       Math.cos(lat2 * (Math.PI / 180)) *
                       Math.cos((lon1 - lon2) * (Math.PI / 180)));
    var miles = (Math.acos(calculation) / (Math.PI / 180)) * 69.09;
    return miles;
}
```

