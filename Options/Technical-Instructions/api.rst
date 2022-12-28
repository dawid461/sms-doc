1. API
++++++

1.1. Account
============
Api "Account" służy do rejestrowania użytkowników w aplikacji SMS oraz do pobierania danych na ich temat.


Endpoint account/register
~~~~~~~~~~~~~~~~~~~~~~~~~
Służy do wysyłania danych nowo utworzonych użytkowników.

* Metoda: POST

* Pobierane parametry::

    {
    "firstName": "string",
    "lastName": "string",
    "email": "string",
    "phone": "string",
    "password": "string",
    "confirmPassword": "string",
    "roles": [
      0
    ]
    }

* Zwracane dane - brak


Endpoint account/{id}
~~~~~~~~~~~~~~~~~~~~~
Pobiera dane użytkownia na podstawie id utworzonego konta.

* Metoda: GET

* Pobierane parametry::

  {id:"int32"}

* Zwracane dane - np. dla id = 1::

    
    "result": {
    "accountId": 1,
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@test.com",
    "phone": "+48 998 998 998",
    "active": true,
    "roles": [
      {
        "id": 1,
        "name": "Administrator"
      }
    ]},
    "errorMessage": null,"timeGenerated": "2022-12-16T12:13:13.7766977Z"


Endpoint account
~~~~~~~~~~~~~~~~
Pobiera pełną liste użytkowników.

* Metoda: GET

* Pobierane parametry - brak

* Zwracane dane::

   "result": [
    { "accountId": 1,
      "firstName": "John",
      "lastName": "Doe",
      "email": "john.doe@test.com",
      "active": true,
      "roles": [
        {
          "id": 1,
          "name": "Administrator"
        }
      ]
    },
    {
      "accountId": 2,
      "firstName": "Consultant",
      "lastName": "consultant",
      "email": "consultant@test.com",
      "active": true,
      "roles": [
        {
          "id": 2,
          "name": "Consultant"
        }
      ]}],
      "errorMessage": null,"timeGenerated": "2022-12-16T12:32:55.6521056Z"


Endpoint account/roles
~~~~~~~~~~~~~~~~~~~~~~
Pobiera rodzaje ról użytkowników w aplikacjii.

* Metoda: GET

* Pobierane parametry - brak

* Zwracane dane::

    "result": [
    {"id": 1,"name": "Administrator"},
    { "id": 2, "name": "Consultant"}],
    "errorMessage": null,"timeGenerated": "2022-12-16T10:58:45.8036735Z"


1.2. Auth
=========
Api "Auth" służy do autoryzowania użytkownika podczas logowania oraz do wylogowania użytkownika.

Endpoint auth/login
~~~~~~~~~~~~~~~~~~~
Wysyła login oraz hasło w czasie logowania w celu autoryzacji użytkownika. Api zwraca token po poprawnym zalogowaniu.

* Metoda: POST

* Pobierane parametry::

  {"email":"string","password":"string"}

* Zwracane dane::

  {"result": {"jwtToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1bmlxdWVfbmFtZSI6IkpvaG4iLCJmYW1pbHlfbmFtZSI6IkRvZSIsIm5hbWVpZCI6IjEiLCJlbWFpbCI6ImpvaG4uZG9lQHRlc3QuY29tIiwicm9sZSI6ImFkbWluaXN0cmF0b3IiLCJuYmYiOjE2NzEyNjk1NDYsImV4cCI6MTY3MTI2OTg0NiwiaWF0IjoxNjcxMjY5NTQ2LCJpc3MiOiJodHRwczovL2xvY2FsaG9zdDo3MjAyIiwiYXVkIjoiaHR0cHM6Ly9sb2NhbGhvc3Q6NzIwMiJ9.Efge7VeF7Q7TACP_bItiaHQi7YwlFC9fBa_foActsbo","refreshToken": "buVXhNg19O4Mhvdt7w20OxUA2Bs/svOefQ7+lf1TjBwAKqe++QmMxftJBzG8ZJYhNK0BMVlEotvYQL8l3/kucA==","expiresDate": "2022-12-17T09:37:26.1014521Z"},"errorMessage": null,"timeGenerated": "2022-12-17T09:32:26.1017855Z"}


Endpoint auth/logout
~~~~~~~~~~~~~~~~~~~~
Wylogowuje aktualnie zalogowanego użytkownika w aplikacji SMS.

* Metoda: POST

* Pobierane parametry - brak.

* Zwracane dane - np.::

  {date: Sat,17 Dec 2022 09:56:30 GMT server: Kestrel }


Endpoint auth/refresh
~~~~~~~~~~~~~~~~~~~~~
odpowiada za odświeżanie tokenu logowania.

* Metoda: POST

* Pobierane parametry - brak.

* Zwracane dane - np.::
  
  {content-type: application/json; charset=utf-8 date: Sat,17 Dec 2022 10:12:16 GMT server: Kestrel} 


Endpoint auth/verify
~~~~~~~~~~~~~~~~~~~~
Weryfikuję wprowadzone dane logowania użytkownika.

* Metoda: POST

* Pobierane parametry - brak.

* Zwracane dane - np.::
  
  {"result": {"accountId": 1,"firstName": "John","lastName": "Doe","email": "john.doe@test.com","active": true,"roles": [{"id": 1,"name": "Administrator"}]},"errorMessage": null,"timeGenerated": "2022-12-17T10:40:54.8227988Z"}




1.3. Campaign
=============
Api "Campaign" odpowiada za tworzenie, filtrowanie oraz pobieranie danych o aktualnie prowadzonych kampaniach.

Endpoint campaign
~~~~~~~~~~~~~~~~~
Odpowiada za tworzenie nowej kampanii i wprowadzenie jej do bazy danych oraz do pobierania danych na temat prowadzonych kampanii.

* Metoda: POST, GET

* Pobierane parametry::

  {"name": "string","type": 0,"customerId": "3fa85f64-5717-4562-b3fc-2c963f66afa6","start": "2022-12-17T14:18:10.222Z","end": "2022-12-17T14:18:10.222Z","records": 0}

* Zwracane dane - brak


Endpoint campaign/{id}
~~~~~~~~~~~~~~~~~~~~~~
Pobiera dane o kampani na podstawie podanego id.

* Metoda: GET

* Pobierane parametry - brak

* Zwracane dane:: 

  {"type": "string","title": "string","status": 0,"detail": "string","instance": "string","additionalProp1": "string","additionalProp2": "string","additionalProp3": "string"}


Endpoint campaign/filter
~~~~~~~~~~~~~~~~~~~~~~~~
Pobiera dane o kampaniach według zadanych filtrów w aplikacji SMS.

* Metoda: GET

* Pobierane parametry - brak

* Zwracane dane::

  {"type": "string","title": "string","status": 0,"detail": "string","instance": "string","additionalProp1": "string","additionalProp2": "string","additionalProp3": "string"}


Endpoint campaign/contact
~~~~~~~~~~~~~~~~~~~~~~~~~
Odpowiada za wprowadzenie do bazy danych kontaktowych osoby odpowiedzialnej za kampanie.

* Metoda: POST

* Pobierane parametry np.::

  {"campaignId": "3fa85f64-5717-4562-b3fc-2c963f66afa6","firstName": "string","lastName": "string","email": "string","phone": "string"}

* Zwracane dane - brak


Endpoint campaign/consultant
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Odpowiada za wprowadzenie do bazy danych id konsultanta odpowiedzialnego za kampanie.

* Metoda: POST
 
* Pobierane parametry np.::

  {"campaignId": "3fa85f64-5717-4562-b3fc-2c963f66afa6","consultantId": "3fa85f64-5717-4562-b3fc-2c963f66afa6"}

* Zwracane dane - brak


Endpoint campaign/{id}/rates
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Wprowadza do bazy danych informację ekonomiczne na temat prowadzonej kampanii.

* Metoda: POST
 
* Pobierane parametry np.::

  {"campaignId": "3fa85f64-5717-4562-b3fc-2c963f66afa6","amount": 0,"quantity": 0,"efficency": 0,"realization": 0}

* Zwracane dane - brak



1.4. Customer
=============
Api "Customer" odpowiada za przechowywanie danych o klientach.

Endpoint customer
~~~~~~~~~~~~~~~~~
Odpowiada za tworzenie rekordu do bazy danych na temat nowego klienta oraz pobieranie danych o już istniejących klientach.

* Metoda: POST, GET
 
* Pobierane parametry::

  {"name": "string","city": "string","zipCode": "string","street": "string"}

* Zwracane dane - brak


Endpoint customer/{id}
~~~~~~~~~~~~~~~~~~~~~~
Zwraca dane na temat klienta na podstawie przesłanego id.

* Metoda: GET

* Pobierane parametry::

  {id:"string"}

* Zwracane dane::

  {"name": "string","city": "string","zipCode": "string","street": "string"}


Endpoint customer/contact
~~~~~~~~~~~~~~~~~~~~~~~~~
Wprowadza dane kontaktowe o kliencie do bazy danych oraz usuwa je w razie potrzeby.

* Metoda: POST, DELETE
 
* Pobierane parametry::

   {"name": "string","city": "string","zipCode": "string","street": "string"}

* Zwracane dane - brak


Endpoint customer/addres
~~~~~~~~~~~~~~~~~~~~~~~~~
Ten endpoint odpowiada za aktualizację danych adresowych klienta

* Metoda: PUT
 
* Pobierane parametry::

   {"name": "string","city": "string","zipCode": "string","street": "string"}

* Zwracane dane - brak



