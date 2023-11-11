# VTEAM - dummy-server med api-routes

Det här repot består av en express-server som innehåller ett antal api-routes (se nedan för detaljer).
Dummy-servern ska användas under utveckling av klienterna i kursen vteam.

Jag har skapat api-routes och modeller som ska likna slutprodukten så långt som möjligt.

## Kom igång
Klona repot och kör ```npm install```.

Starta servern med ```npm run start``` från roten av repot.

Alternativet är att starta den via docker. Då startar du den med ```docker-compose up --build``` från roten av repot.

I båda fallen kommer du åt servern på ```localhost:1338/<route>```

## Routes

För att testa API:ets routes, föreslår jag att du jobbar i Postman. Detta gäller framförallt routes som inte är GET-routes.

### Auth-routes

Skapa ny admin-användare med:
```
POST /register
```
Request-objektet måste innehålla ett objekt med nycklarna:

* email
* password

________________________________________________________________

Logga in med admin-användare och få tillbaka token:
```
POST /login
```
Request-objektet måste innehålla ett objekt med nycklarna:

* email
* password

________________________________________________________________

### Bike-routes

Hämta alla cyklar:
```
GET /bikes
```
________________________________________________________________

Hämta en cykel:
```
GET /bikes/:id
```
________________________________________________________________

Uppdatera en cykel (ej klar):
```
PUT /bikes/:id
```
Request-objektet måste innehålla ett bike-objekt med nycklarna:

* city_id
* status_id
* geometry (array med lat och long)
________________________________________________________________

Hyr en cykel (ej klar):
```
POST /bikes/:id/rent
```

När rent-routen anropas ska följande hända
* Cykelns status ska ändras
* En trip skapas (user_id, bike_id, starttid, startposition)
* När skickar vi in värden för cost-attributen?

________________________________________________________________

Avsluta cykeltur (ej klar):
```
POST /bikes/:id/return
```

När return-routen anropas ska följande hända:
* Cykelns status ska ändras
* En trip uppdateras (sluttid, slutposition)
* När skickar vi in värden för cost-attributen?
* Kundens saldo ändras

________________________________________________________________

### City-routes

Hämta alla städer:
```
GET /cities
```
________________________________________________________________

Hämta en stad:
```
GET /cities/:id
```
________________________________________________________________

Lägg till en stad:
```
POST /cities
```



________________________________________________________________