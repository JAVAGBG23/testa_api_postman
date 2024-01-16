# postman-testing-student-api

### Exempel på hur du kopplar MongoDB till Spring Boot och gör enkla queries (CRUD).

## API

#### POST - Skapa en blog post
http://localhost:8080/blogpost

Börja med att skapa ett par bog posterl genom att använda Postman. Du kan kopiera eller skapa en blog post enligt följande:

{
    "title": "Spring Boot TWO",
    "content": "content from Spring Boot TWO"
}

Se till att göra en POST request och skicka med bodyn som JSON raw.

### GET - Blog post med exakt id
http://localhost:8080/blogpost/{id}

Kopiera en blog postens id, OBS! endast id inte hela ObjectId. Byt ut {id} till det id du kopierade och gör en GET request.
getById() är en metod som vi får av MongoDB kommer att returnera ett objekt ifrån från student collection, alltså den blog post som matchar med det id som vi skickar med.

### GET - Hämta alla blog posts
http://localhost:8080/blogposts

Hämta alla document i vår BlogPost collection. Vi använder List här i vår controller och vår service metod för att kunna returnera mer än ett dokument från vår
collection. Om du har extremt myclet dokument i din databas bör du ta dig en funderare på hur du använder findAll() metoden, du skulle säkerligen behöva skriva lite mer kod.
findAll() får vi från MongoDB.

### PUT - Uppdatera en blog post
http://localhost:8080/update

Här lägger vi vår unika identifier i vår request body och inte direkt i vår URL. Vi hade kunnat lägga den i vår URL likt getById() men då hade vi inte fått
möjligheten att faktiskt skapa en ny blog post om ingen unik identifier bifogas. Så det här är egentligen spara eller uppdatera berodende på om vi skickar  med 
något id eller inte i vår request body. 
Exempel:

{
        "id": "65a5446bd67b83358eb79839",
        "title": "UPDATED",
        "content": "content from Spring Boot TWO",
        "created_at": "2024-01-15T14:42:51.315+00:00",
        "posted_by": "Helena"
}

### DELETE - Ta bort en student
http://localhost:8080/blogpst/{id}

Här gör vi precis som i findById(), vi lägger till det unika id för vår student som vi vill ta bort i vår URL. Vi lägger id i URL path alltså => @PathVariable
Vi returnerar ett meddelande istället för att returnera den borttagna blog posten.


