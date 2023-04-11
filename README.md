Abrufen in: video>movieDetails

1. Rufe alle Filme ab, bei denen der Regisseur Steven Spielberg ist und gib nur das Feld 'Titel' aus.
   **db.movieDetails.find({director:"Steven Spielberg"},{title:1, \_id:0})**

2. Rufe alle Filme ab, bei denen die Anzahl der Benutzerbewertungen bei Rotten Tomatoes mehr als 40000 ist.Beschränke die Suche auf 20 Filme und sortiere sie absteigend nach Benutzerbewertungen.
   **db.movieDetails.find({"tomato.userReviews":{$gte:40000}}).sort({"tomato.userReviews":-1}).limit(20)**

3. Rufe alle Filme ab, die zwischen 2000 und 2005 gedreht wurden (beide Jahre eingeschlossen) und gib nur die Felder 'Titel' und 'Jahr' aus.
   **db.movieDetails.find({year:{$gte:2000,$lte:2005}},{title:1, year:1, \_id:0})**

4. Rufe alle Filme ab, die eine Rotten Tomatoes Benutzerbewertung von mindestens 4 haben und nach 2010 entstanden sind. Gib nur die Felder 'Titel' und 'Regisseur' aus."
   **db.movieDetails.find({"tomato.rating":{$gt:4}, year:{$gt:2010}},{title:1, director:1, \_id:0})**

5. Rufe alle Filme ab, die weniger als 1000 Benutzer-Rezensionen bei Rotten Tomatoes haben und vor dem Jahr 2005 gedreht wurden. Sortiere sie aufsteigend nach der Anzahl der Benutzer-Rezensionen und beschränke die Suche auf 10 Filme.
   **db.movieDetails.find({"tomato.userReviews":{$lt:1000}, year:{$lt:2005}}).sort({"tomato.userReviews":1}).limit(10)**

6. Rufe alle Filme ab, die das Feld 'Rotten Tomatoes' nicht enthalten.
   **db.movieDetails.find({'Rotten Tomatoes':{$exists:false}})**

7. Rufe alle Filme ab, die mindestens 100 IMDb-Stimmen, aber weniger als 1000 haben und gib nur die Felder 'Titel' und 'IMDb Bewertung' aus.
   **db.movieDetails.find({"imdb.votes":{$gte:100,$lt:1000}},{title:1, "imdb.rating":1, \_id:0})**

8. Sortiere alle Filme absteigend nach ihrer IMDb-Bewertung.
   **db.movieDetails.find({}).sort({"imdb.rating":-1})**

9. Rufe die 10 Filme mit der höchsten IMDb-Bewertung ab, sortiert in absteigender Reihenfolge.
   **db.movieDetails.find({"imdb.rating":{$lte:10}}).sort({"imdb.rating":-1}).limit(10)**

10. Rufe alle Filme mit den Genres 'Crime' und 'Drama' ab und gib nur die Felder 'Titel' und 'Genre' aus. Sortiere sie aufsteigend nach ihrer IMDb-Bewertung."
    **db.movieDetails.find({genres:{$in:['Crime','Drama']}},{title:1,genres:1,\_id:0}).sort({"imdb.rating":1})**

    **db.movieDetails.find({$and:[{genres:{$in:['Crime']}},{genres:{$in:['Drama']}}]},{title:1,genres:1,\_id:0}).sort({"imdb.rating":1})**
