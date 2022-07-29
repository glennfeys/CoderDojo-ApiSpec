


## Entiteiten:

`*` == verplicht veld

<span style="text-decoration:underline;">User</span>



*   *user_id
*   *firstname
*   *lastname
*   password
*   email
*   gender
*   birth_date
*   registration_date
*   address
*   *language: mogelijke waarden uit endpoint
*   phone_number
*   *wants_mail
*   *is_admin
*   profile_picture
*   *picture_permission
*   special_info
*   archived

<span style="text-decoration:underline;">Dojo</span>



*   *dojo_id
*   *name
*   *description
*   *email
*   profile_picture
*   *address (postcode, city, street, address_number, country)
*   *archived
*   *languages

<span style="text-decoration:underline;">Event</span>



*   *event_id
*   *name
*   *description
*   *dojo
*   *from_date
*   *to_date
*   registration_deadline
*   *visible
*   *cancelled

<span style="text-decoration:underline;">Session</span>



*   *session_id
*   *event_id
*   *name
*   *description
*   laptop_amount
*   *capacity
*   min_age
*   max_age
*   tags
*   archived

<span style="text-decoration:underline;">Misschien: Task</span>



*   Feedback gevraagd

<span style="text-decoration:underline;">Role</span>



*   *role_id
*   Name
*   description

<span style="text-decoration:underline;">UserRole</span>



*   *user_id
*   *role_id
*   *dojo_id

<span style="text-decoration:underline;">Inschrijving: User -> Session</span>



*   *user_id
*   *session_id
*   *registration_time
*   *in_queue
*   *needs_laptop
*   present
*   *cancelled

<span style="text-decoration:underline;">Inschrijving Coach -> Event</span>



*   *user_id
*   *event_id
*   *registration_time
*   *cancelled
*   present


## Endpoints:



*   Dojo overview
*   Mogelijke talen

Root:



*   GET 		/

Users:



*   GET 		/users
*   POST 		/users

User:



*   GET 		/users/{id}
*   PUT		/users/{id}
*   PATCH 	/users/{id}
*   DELETE	/users/{id}

Dojos:



*   GET		/dojos
*   POST		/dojos

Dojo:


*   GET   /dojos/{id}
*   PUT		/dojos/{id}
*   PATCH 	/dojos/{id}
*   DELETE	/dojos/{id}

Events:



*   GET		/events
*   POST		/events

Event:


*   GET   /events/{id}
*   PUT	 	/events/{id}
*   PATCH 	/events/{id}
*   DELETE	/events/{id}

Sessions:



*   GET		/sessions
*   POST		/sessions

Session:


*   GET   /sessions/{id}
*   PUT	 	/sessions/{id}
*   PATCH 	/sessions/{id}
*   DELETE	/sessions/{id}
