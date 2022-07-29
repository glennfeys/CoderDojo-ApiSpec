# Vergadering 3

Locatie: Discord (online)

Datum: 18/03/2020 om 14:00

Aanwezig: Glenn, Django, Lucianos, Liouka, Robbe

Voorzitter: Django

Notulist: Glenn Feys


## Agendapunten

* Authenticatie-methode vastleggen
* Endpoints voor registratie (bv nieuwe gebruiker, ww bevestigen)
* Endpoint voor inloggen
* Inschrijven coach/ninja voor events en sessies
* Endpoints voor rapportering

## Verslag

* bestand opslplitsen maar ook volledig bestand houden voor de editor te kunnen gebruiken
* verschillende response schemas per rol ?
* Appart address veld voor users zonder coordinates
* Gender issue is een non-issue
* coordinaten aanpassen naar laurens zijn idee
* alle errors op hetzelfde niveau houden en dus adress errors aanpassen
* archiveren lijkt ons genoeg geen status meegeven gewoon doen alsof dit verwijderd is.
* bij registreren eerst geen wachtwoord ingeven en pas wachtwoord gebruiker bij confirmatie
* het formaat van de error responses zal aangepast worden naar het volgende formaat:

    ```
    {
        "message",
        "fields": : {
            "name": "cannot be empty",
            "email": "taken",
            ...
        }
    }
    ```
    
## Besluiten
- Unauthorized enkel voor volledige routes die niet gezien kunnen worden.

- Geen logout nodig, zelfde als JWT vergeten en redirect naar homepagina. (enkel frontend).

- Verschillende responses afhankelijk van authorizatie zullen we waarschijnlijk doen met `oneOf`

- Misschien eens vragen aan coder dojo of ons coach application systeem goed is.



## Endpoints

### /tags (GET/POST/PUT/DELETE)
CRUD operaties op tags

### /technologies
(kan vervangen worden door tags en wordt voorlopig enkel gebruikt voor ranks die er eigenlijk nog niet in moeten.)

### /users?subscription={dojoID}
toon users die subscribed zijn op dojo (gewoon extra filter aan `GET /users` toevoegen)

### /users/{id}/dojo-subscriptions (GET/POST)
toont alle dojos waarop iemand subscribed is

### ~~/users/logout~~
Dit wordt client-side afgehandeld door de webtoken weg te smijten

### /users/login (POST)
* email
* password
#### Response
* User/error
* webtoken
* refreshtoken

### /users/refresh (POST)
na x tijd vervalt de webtoken en moet een nieuwe aangevraagd worden
* webtoken
* refreshtoken
#### Response
* OK/error
* webtoken
* refreshtoken

### /users/verify (POST)
wordt gebruikt voor het verifiëren van email/wachtwoord vergeten/kind loskoppelen voor het confirmen van de actie en het passwoord aan te passen
* token
* password
#### Response
* User/error
* webtoken
* refreshtoken

### /users/reset-password
Stuur een mail om het wachtwoord opnieuw in te stellen
* email
#### Response
* succes/error

### /dojos/{id}/users (GET/POST)
Lijst met alle rollen in een dojo/iemand rol geven in dojo
(voor POST)
* role
* userId
#### Response
* succes/error

### /dojos/{id}/users/{id} (GET/PATCH/DELETE)
rol van een user binnen een dojo
(voor PATCH)
* role
#### Response
* succes/error

### /dojos/{id}/applications (POST/GET)
meld je aan om coach te worden van deze dojo/ lijst van applications
* message
* userId
#### Response
* succes/error/applications

### /dojos/{id}/applications/{id} (GET/PUT/DELETE)
meld je aan om coach te worden van deze dojo/ lijst van applications
* userId
* message
* status (enum)
    * Pending
    * Accepted
    * Refused
#### Response
* succes/error/application

### /tickets (GET/POST)
lijst van de tickets (voor coaches en ninjas)
* userId
* eventId
* sessionId
* needsLaptop
* role

### /tickets /{id} (GET/PUT/PATCH/DELETE)
CRUD voor een ticket
* userId
* eventId
* sessionId
* needsLaptop
* role
* status (enum)
    * Present
    * NotPresent
    * Cancelled
    * Waiting
    * InQueue
#### Response
* Ticket/error


## Rapportering

### /report/dojos (GET)
#### filters
* timescale
* dateMin
* dateMax
* city
* country
* tags
* languages
* archived

#### Response
```json
[
    {
        startTime: date-time,
        endTime: date-time,
        amount: int
    }
]
```

### /report/users (GET)
#### filters
* timescale
* dateMin
* dateMax
* subscribedDojoId
* registeredDojoId
* archived

#### Response
```json
[
    {
        startTime: date-time,
        endTime: date-time,
        amount: int
    }
]
```

### /report/events (GET)
#### filters
* timescale
* dateMin
* dateMax
* dojoId
* cancelled
* archived

#### Response
```json
[
    {
        startTime: date-time,
        endTime: date-time,
        amount: int
    }
]
```

### /report/sessions (GET)
#### filters
* minAge
* maxAge
* eventId
* dojoId
* tags
* technologies
* archived

#### Response
```json
[
    {
        startTime: date-time,
        endTime: date-time,
        amount: int
    }
]
```

### /report/tickets (GET)
#### filters
* timescale
* dateMin
* dateMax
* role
* dojoId
* eventId
* sessionId
* userId
* status

#### Response
```json
[
    {
        startTime: date-time,
        endTime: date-time,
        amount: int
    }
]
```


## Taakverdeling

Wie een taak wilt/kan doen assignt zichzelf voor de bijhorende issue op GitHub.

| Verantwoordelijken | Taak               | Deadline |
| ------------------ |:------------------ |:--------:|
| Liouka             | Errors             |  23/03   |
| Lucianos           | Rapportering       |  23/03   |
| Django             | Tickets            |  23/03   |
| Robbe              | Openstaande issues |  23/03   |


## Datum volgende vergadering

Onbepaald (tot issues ontstaan)
