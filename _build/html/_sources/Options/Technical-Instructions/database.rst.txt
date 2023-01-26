2. Bazy danych
++++++++++++++

2.1. db.powiadomienia
=====================
Odpowiada za powiadomienia systemowe w aplikacji SMS.

   .. image:: /Media/database/db_notifications.png
        :width: 600

2.1.1 dbo.Notification
----------------------
Reprezentuje dane notyfikacji systemowej
    * Id: unikalny identyfikator [guid]
    * CreatorId: unikalny identyfikator użytkownika który utworzył wiadomość [guid]
    * Tilte: tytuł wiadomości [nvarchar]
    * Body: wiadomość [nvarchar]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]
    
2.1.2 dbo.Notifications
-----------------------
Reprezentuje zbiór wiadomości wysłanych do użytkowników systemu
    * NotificationId: unikalny identyfikator [guid]
    * UserId: unikalny identyfikator użytkownika [guid]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.1.3 dbo.NotificationHistory
-----------------------------
Reprezentuje historię utworzonej notyfikacji systemowej
    * Id: unikalny identyfikator [guid]
    * NotificationId: unikalny identyfikator notyfikacji [guid]
    * UserId: unikalny identyfikator użytkownika [guid]
    * Type: rodzaj zdarzenia [int]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.1.4 dbo.Groups
----------------
Reprezentuje grupy kontaktowe
    * Id: unikalny identyfikator [guid]
    * Name: nazwa grupy [nvarchar]
    * Description: opis [nvarchar]
    * GroupType: rodzaj grupy kontaktowej [int]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.1.5 dbo.ContactGroups
-----------------------
Reprezentuje użytkowników przypisanych do grup kontaktowych 
    * UserId: unikalny identyfikator użytkownika [guid]
    * GroupId: unikalny identyfikator grupy [guid]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]


2.2. db.identity
================
Link do dokumentacji Microsoftu: 
``https://learn.microsoft.com/pl-pl/aspnet/core/security/authentication/identity?view=aspnetcore-7.0&tabs=visual-studio``

   .. image:: /Media/database/db_identity.png
        :width: 600

Nazwy tabel z linkami do dokumentacji Microsoftu:
-------------------------------------------------
    * AspNetUsers: ``https://learn.microsoft.com/pl-pl/dotnet/api/microsoft.aspnetcore.identity.entityframeworkcore.identityuser?view=aspnetcore-1.1``
    * AspNetUserTokens: ``https://learn.microsoft.com/pl-pl/dotnet/api/microsoft.aspnetcore.identity.entityframeworkcore.identityuserlogin-1?view=aspnetcore-1.1``
    * AspNetUserLogins: ``https://learn.microsoft.com/pl-pl/dotnet/api/microsoft.aspnetcore.identity.entityframeworkcore.identityuserlogin-1?view=aspnetcore-1.1``
    * AspNetUserClaims: ``https://learn.microsoft.com/pl-pl/dotnet/api/microsoft.aspnetcore.identity.entityframeworkcore.identityuserclaim-1?view=aspnetcore-1.1``
    * AspNetUserRoles: ``https://learn.microsoft.com/pl-pl/dotnet/api/microsoft.aspnetcore.identity.entityframeworkcore.identityuserrole-1?view=aspnetcore-1.1``
    * AspNetRoles: ``https://learn.microsoft.com/pl-pl/dotnet/api/microsoft.aspnetcore.identity.entityframeworkcore.identityrole?view=aspnetcore-1.1``
    * AspNetRoleClaims: ``https://learn.microsoft.com/pl-pl/dotnet/api/microsoft.aspnetcore.identity.entityframeworkcore.identityroleclaim-1?view=aspnetcore-1.1``


2.3. db.kampanie
=================

odpowiada za przechowywanie danych o prowadzonych kampaniach sprzedażowych.
   
   .. image:: /Media/database/db_campaigns.png
        :width: 600

2.3.1 dbo.Campaigns
-------------------
Reprezentuje kampanie sprzedażowe zarejestrowane w systemie
    * Id: unikalny identyfikator [guid]
    * Name: nazwa kampanii [nvarchar]
    * Type: rodzaj kampanii [int]
    * CustomerId: unikalny identyfikator przypisanego klienta [guid]
    * Start: data rozpoczęcia [datetime]
    * End: data zakończenia [datetime]
    * Records: liczba zadanych rekordów [int]
    * State: status aktywny/nieaktywny []
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.3.2 dbo.Rates
---------------
Reprezentuje cele sprzedażowe przypisane do kampanii
    * Id: unikalny identyfikator [guid]
    * Amount: zadana wartość wyrażona w PLN [decimal]
    * Quantity: zadana ilość wyrażona w sztukach [decimal]
    * Efficiency: efektywność wyrażona w % [decimal]
    * Realization: zadany procent realizacji wyrażona w %  [decimal]
    * CampaignId: unikalny identyfikator przypisanej kampanii [guid]
    * ConsultantId: unikalny identyfiaktor przypisanego konsultanta [guid]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.3.3 dbo.Consultants
---------------------
Reprezentuje konsultantów przypisanych do kampanii sprzedażowej
    * Id: unikalny identyfikator [guid]
    * CampaignId: unikalny identyfikator przypisanej kampanii [guid]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.3.4 dbo.Scores
----------------
Reprezentuje wyniki sprzedażowe przypisane do konsultanta oraz kampanii sprzedażowej
    * Id: unikalny identyfikator [guid]
    * ConsultantId: unikalny identyfiaktor przypisanego konsultanta [guid]
    * CampaignId: unikalny identyfikator przypisanej kampanii [guid]
    * RecordId: unikalny identyfikator rekordu [guid]
    * CallStatus: Status połączenia [int]
    * ConnectionDate: Data połączenia [datetime]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.3.5 dbo.ScoreCustomFields
---------------------------
Reprezentuje konfigurowalne pola powiązane z wynikiem sprzedażowym
    * Id: unikalny identyfikator [guid]
    * Name: Nazwa pola: [nvarchar]
    * Description: opis pola [nvarchar]
    * Type: rodzaj pola [int]
    * ScoreId: unikalny identyfikator wyniki sprzedażowego [guid]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.3.6 dbo.Customers
-------------------
Reprezentuje dane klienta powiązanego z kampanią sprzedażową
    * Id: unikalny identyfikator [guid]
    * Name: nazwa klienta [ nvarchar]
    * AddressId: unikalny identyfikator przypisanego adresu [guid]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.3.7 dbo.Addresses
-------------------
Reprezentuje adres przypisany do klienta
    * Id: unikalny identyfikator [guid]
    * City: miasto [nvarchar]
    * ZipCode: kod pocztowy [nvarchar]
    * Street: ulica [nvarchar]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]

2.3.8 dbo.Contacts
------------------
Reprezentuje adres przypisany do klienta
    * Id: unikalny identyfikator [guid]
    * FirstName: imię [nvarchar]
    * LastName: nazwisko [nvarchar]
    * Email: adres email [nvarchar]
    * Phone: numer telefony [nvarchar]
    * CustomerId: unikalny identyfiaktor przypisanego klienta [guid]
    * CampaignId: unikalny identyfikator przypisanej kampanii [guid]
    * State: status aktywny/nieaktywny [bool]
    * CreatedAt: data utworzenia [datetime]
    * ModifiedAt: data modyfikacji [datetime]




