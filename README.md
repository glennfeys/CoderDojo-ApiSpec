# 2019-2020-rest-api

## Giving feedback
To give comments or feedback on the API design, please open an issue on Github

## Viewing the documentation

Unfortunately we had some problems with generating html docs for the specification, so we recommend
viewing the specification via the Swagger editor:
* Go to https://editor.swagger.io/
* Open the specification via `File` -> `Import file`

Alternatively, you can view the specification locally via [swagger-ui-watcher](https://www.npmjs.com/package/swagger-ui-watcher):
* open a terminal in the repo root directory
* ```npm install swagger-ui-watcher -g```
* ```swagger-ui-watcher api_specs/openapi.yaml```

Make sure you __ALWAYS__ run the command with the file `openapi.yaml`. This will show the documentation for the entire API.

## Change log v1.1.4
* Changed:
  * leads can see all users
  * status code of reset-password and verify (200->204)

## Change log (14/04/2020) v1.1.3
* Added:
  * `region` and `technologyIds` filter to `GET /events`

## Change log (12/04/2020) v1.1.2
* Changed:
  * Made `cancelled` in sessions boolean instead of string
  * EventParticipationsList so that `_embedded` and `_links` are used
* Removed:
  * `timescale` query parameter from `/reports/event-participations` endpoint
* Added:
  * Delete to ninja ticket and coach ticket routes
  * Count to every GET response on collection

## Change log (08/04/2020) v1.1.1
* Changed:
  * Made only zip code in user's address mandatory
  * Phone number is now required for normal users (not children)
  * `globalRole` to `globalRoles` in user
* Added:
  * `laptopAmount` field to dojos
  * `region` field to dojo and user address
  * `archived` field to ninja and coach tickets
  * Endpoints `/reports/event-participations` to make it possible to request a list of users with the amount of events they have participated in.
  * Region and zip code query parameter to the report endpoints.
  * Links in root for subscriptions and dojo-roles
  * Link in dojo for roles


## Change log (01/04/2020) v1.1.0
### Milestone 2
* Added:
  * Endpoints for tickets for events/sessions
  * Endpoints for technologies + needed (error) schemas
  * Endpoints for tags + needed (error) schemas
  * Endpoints for applications as coach for dojos + needed (error) schemas
  * Reporting endpoints for dojos, users, events, sessions and tickets
  * Endpoints for authentication
  * Authorisation on all endpoints where needed
  * Endpoints for subscribing users to dojo's
  * Endpoints for roles in dojo's
  * split up files (how to see docs see above)
  * Email must be given in request to detach child
  * eventPost and sessionPost link in dojo/event
  * global role field to `User` to indicate whether they are admin or normal user
  * `archived` field to `User`, `Dojo`, `Event` and `Session`
  * `cancelled` field to `Session`
  * Root route for reports
* Removed:
  * `laptopsAvailable` property in EventError response
  * `status` property in Error response
  * Nested adress error
  * Coordinates out of user address
  * Ability to change email after sign up
* Changes:
  * Moved field error messages to separate `fieldErrors` property in error responses
  * Field error messages concerning addresses are no longer nested as objects in error responses
  * `other` to `o` in Gender
  * coordinates to an object:
  ```
  {
      latitude: float,
      longitude: float
  }
  ```
  * Made `dateOfBirth` a required field in `User`

### Release notes
#### Authentication
We decided to use JWT's to implement authorisation, this way people can use a standard as OAuth2 but they can also implement their own authentication.
There is no logout route because a logout can be handled in the frontend by forgetting the JWT token.
The refresh route is to renew the session.
The verify route is a versatile route that can be used for setting/resetting password. This is used for sign up aswell.

Signup flow:
  - users gives in all info except for password
  - user gets email te complete account and verify email
  - user clicks link and gives password to complete account
child detach flow:
  - child detach is requested with email of child
  - email is send to email of child
  - child completes detachment by filling in password and completing his account
password reset flow:
  - user requests password reset of account with given email
  - password reset link is clicked on email
  - user gives in new password

#### Authorisation
*IMPORTANT* _links differ a lot for each role but are not explicitly given per role. So developers have to check what links they have to send for each role. links are only send if they can in fact perform the action.    
The roles that can do calls to the endpoints are given with the x-roles field
if there are certain fields or things that differ per role that is specified in the descriptions.
Sometimes there might be things unclear or unknown still please contact your API team member in that case or make an issue.

#### Reporting
there are new reporting endpoints that work without pagination, they give a list of aggregate data about the entities requested.
You can give an interval and a step size that way you can easily get data to make graphs and such with this endpoint.


## Change log (05/03/2020) v1.0.2

* Added:
  * Coordinates to address
  * Specific address errors
  * Fix tags (now only in session/dojo)
  * Pagination Links (next, prev, first, last)
  * Dojo ID as query parameter for GET to `/events`
  * Event ID as query parameter for GET to `/sessions`
  * Description for order param with fields to order by

* Changes:
  * Language string format is now ISO 639-1
  * Made operation IDs more consistent
  * Creating an event is now done via a POST to `/events`
  * Creating a session is now done via a POST to `/sessions`

* Removed:
  * PatchError and replaced with specific errors like in put/post
  * Registration deadline
  * isAdmin field for users
  * picture URL for dojos
  * Pagination headers
  * `/events/{id}/sessions` endpoint
  * `/dojos/{id}/events` endpoint
  * Password in User

## Change log (01/03/2020) v1.0.1

* Added:
  * Use of JSON HAL format for responses
  * Error messages
  * Pagination in headers via `Link` parameter
  * More query parameters
  * `ticketsAvailable` field to Session
  * `/dojos/{id}/events`
  * `/users/{id}/children`
  * More filtering options for lists
* Changes:
  * To detach a child from a user send a `PATCH` request to the `/users/{id}/children` endpoint.
  * To create a new session for an event send a `POST` request to the `/events/{id}/sessions` endpoint.
  * To create a new event for a dojo send a `POST` request to the `/dojos/{id}/events` endpoint.
  * Migrated from snake_case to camelCase
  * `post_code` => `zipCode`
  * All `id`'s  are now string
  * Moved laptop amount from Session to Event
  * `minRecommendedAge` => `minAge`
  * `maxRecommendedAge` => `maxAge`
* Removed:
  * `Rank`
  * `Ticket`
  * `wants_mail` field of user
  * `/events/{id}/tickets`
  * Parent endpoint
* New:
  * The API now allows to filter users on city, zip code and country
