**Verslag vergadering 1**

Locatie: Sterre S5, Projectlokaal 2.1

Datum: 19/02/2020 om 11:30

Aanwezig: Lucianos, Glenn, Robbe, Liouka, Django

Voorzitter: Django

Notulist: Robbe

<span style="text-decoration:underline;">Agendapunten:</span>

Overzicht van de te behandelen punten



*   Entiteiten en endpoints vastleggen/bespreken
*   Velden per entiteit vastleggen/bespreken
*   Swagger hub account aanmaken + organisatie maken
*   Hoe algemeen moet de  api zijn (Best implementatie zo vrij mogelijk houden ?)
*   Hoe stellen we hiërarchie van de roles voor.
*   Authenticatie in de API (Json webtokens)
*   Taakverdeling (misschien per entiteit)
*   Volgende meeting vastleggen

**Verslag:**

Zie ook apart document met entiteiten en endpoints



*   Authenticatie backend en frontend gelijk, geen extra informatie afschermen in backend.
*   Gebruik swaggerhub (document opstellen + organisatie aanmaken) om samen te werken aan de yaml file.
*   Inschrijven event en session. Sowieso session. Eventueel aantal inschrijvingen per event bijhouden als som van inschrijvingen sessions en event. Eventueel gebruik van subsession? Momenteel enkel inschrijven bij een session -> geen inschrijvingen event.
*   Uitzoeken welke (persoonlijke) informatie moet zichtbaar zijn voor wie.
*   Geen meerdere ouders per kind
*   Dynamisch talen bijhouden, zorgen dat nieuwe talen eenvoudig kunnen toegevoegd (of verwijderd) worden.
*   Gebruiker archiveren, niet verwijderen.
*   Momenteel event koppelen aan een dojo, maar dit is niet noodzakelijk (nation or regionwide events).
*   Naast laptops ook nog andere equipment mogelijkheid beschikbaar stellen.
*   Willen we een aparte Task entiteit? Feedback van groepsleden gevraagd.

    Task die makkelijk hergebruikt kan worden, geen duplicatie in databank.

*   Overerving permissions van roles. (lead -> coach -> ninja)
*   Rekening houden met het feit dat ninjas ook coaches kunnen zijn, dus hiermee oppassen bij inschrijvingen.
*   Coaches registreren per event, ninjas per event momenteel.

**Taakverdeling:**

Deadline: Zondag 23 feb 2020

Endpoints + entiteiten:
*   Lucianos: Users
*   Robbe: Dojo’s
*   Liouka: Sessions
*   Glenn: Events
*   Django: Users, ...

**Datum volgende vergadering:**

Nog te bepalen
