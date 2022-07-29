## Verslag vergadering 2

Locatie: Sterre S5, Projectlokaal 2.3

Datum: 04/03/2020 om 11:30

Aanwezig: Iedereen + Professor Goedgebeur

Voorzitter: Glenn

Notulist: Liouka

### Agendapunten:

Overzicht van de te behandelen punten

*   Overlopen API
*   Geneste routes (dojos/id/events en events/id/sessions) vs algemene routes met filters
*   Discussie PUT en PATCH (geen gebruik van PUT voor te updaten?)
*   Parent route nodig ? hoe best parent/children probleem oplossen ?
*   Beste manier voor authenticatie op de API Json web token vs session token
*   Gebroken gegenereerd html documentatie bespreken

### Verslag:

*   is_admin uitbreidbaarder maken -> veld verwijderen en houden voor milestone 2
*   picture urls wegdoen -> veld verwijderen en  houden voor milestone 2
*   parent route lijkt nuttig om te hebben -> houden voor milestone 2
*   algemene routes met filters zijn logischer
    *   Route voor opvragen events van een dojo -> filter op GET /events met dojo ID in request URL.
    *   Route voor toevoegen events aan een dojo -> POST op /events met dojo URL in request body
    *   Route voor opvragen sessions van een event -> filter op GET /sessions met event ID in request URL.
    *   Route voor toevoegen sessions aan een event -> POST op /sessions met event URL in request body
*   PUT lijkt nuttig om te hebben naast PATCH -> PUT laten
*   Gebroken documentatie verwijderen, duidelijk maken in README.md hoe deftig documentatie bekijken via Swagger editor

### Taakverdeling:

<table>
  <tr>
   <td><strong>Persoon</strong>
   </td>
   <td><strong>Taak</strong>
   </td>
   <td><strong>Deadline</strong>
   </td>
  </tr>
  <tr>
   <td>Lucianos
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Robbe
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Django
   </td>
   <td>Alles
   </td>
   <td>4/03/2020
   </td>
  </tr>
  <tr>
   <td>Glenn
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Liouka
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
</table>


### Datum volgende vergadering:

Nog te bepalen