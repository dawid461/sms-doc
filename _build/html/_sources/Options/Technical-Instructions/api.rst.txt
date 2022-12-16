API
+++

Account
=======
Api "Account" służy do rejestrowania użytkowników w aplikacji SMS.


Endpoint account/register
~~~~~~~~~~~~~~~~~~~~~~~~~
Służy do wysyłania danych nowo utworzonych użytkowników.

* Pobierane parametry - brak.
* Zwracane dane

    .. image:: /Media/api/account/account-register.png
        :width: 190

* Modele danych

     .. image:: /Media/api/account/account-register.png
        :width: 190


Endpoint account/{id}
~~~~~~~~~~~~~~~~~~~~~
Pobiera dane użytkownia na podstawie id utworzonego konta.

* Pobierane parametry np. dla id = 1::

    {"result": {
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
    ]},"errorMessage": null,"timeGenerated": "2022-12-16T12:13:13.7766977Z"}

* Zwracane dane - brak

* Modele danych:

     .. image:: /Media/api/account/id.png
        :width: 190


Endpoint account
~~~~~~~~~~~~~~~~
Pobiera pełną liste użytkowników.

* Pobierane parametry::

    {"result": [
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
      ]}],"errorMessage": null,"timeGenerated": "2022-12-16T12:32:55.6521056Z"}

* Zwracane dane - brak

* Modele danych - brak


Endpoint account/roles
~~~~~~~~~~~~~~~~~~~~~~
Pobiera rodzaje ról użytkowników w aplikacjii.

* Pobierane parametry::

    {"result": [
    {"id": 1,"name": "Administrator"},
    { "id": 2, "name": "Consultant"}],
    "errorMessage": null,"timeGenerated": "2022-12-16T10:58:45.8036735Z"}

* Zwracane dane - brak

* Modele danych - brak
