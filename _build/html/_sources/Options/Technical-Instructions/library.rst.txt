Biblioteki
++++++++++

Interfejs
=========

Apis
----
IAccountApi
~~~~~~~~~~~
Kod::

    export interface RegisterCommand {
    firstName: string;
    lastName: string;
    email: string;
    password: string;
    confirmPassword: string;
    phone?: string;
    roles: number[];
    }

    export interface UpdateCommand {
    firstName: string;
    lastName: string;
    email: string;
    phone: string;
    roles: Role[];
    active: boolean;
    }

    export interface IAccountApi {
    register: (command: RegisterCommand) => Promise<Response<string>>;
    getById: (id: number) => Promise<Response<Account>>;
    getAll: () => Promise<Response<Account[]>>;
    getRoles: () => Promise<Response<Role[]>>;
        }

IAuthApi
~~~~~~~~
Kod::

    export interface VerifyResponse
    extends Response<{
        firstName: string;
        lastName: string;
        email: string;
        roles: { id: number; name: string }[];
    }> {}

    interface IAuthApi {
    login: (email: string, password: string) => Promise<Response<void>>;
    logout: () => Promise<Response<void>>;
    refresh: () => Promise<Response<void>>;
    verify: () => Promise<VerifyResponse>;
    }

ICampaignApi
~~~~~~~~~~~~
Kod::

    interface ICampaignApi {
    getById: (id: string) => Promise<Response<CampaignDetails>>;
    getAll: () => Promise<Response<Campaign[]>>;
    getByFilter: (query: CampaignFilterQuery) => Promise<Response<Campaign[]>>;
    }

IHttpClient
-----------
Kod::

    interface IHttpClient {
    get: <T>(url: string, params?: any) => Promise<T>;
    post: <T>(url: string, body?: {}) => Promise<T>;
    put: <T>(url: string, body?: {}) => Promise<T>;
    delete: <T>(url: string) => Promise<T>;
    }

INotificationProvider
---------------------
Kod::
    
    interface INotificationProvider {
    display: (message: string, type: NotificationType) => void;
    }


Modele danych
=============

Account
-------

Account
~~~~~~~
Kod::

    interface Account {
    firstName: string;
    lastName: string;
    email: string;
    roles: string[];
    }


AccountDetails
~~~~~~~~~~~~~~
Kod::

    interface AccountDetails {
    id: string;
    phone: string;
    active: boolean;
    firstName: string;
    lastName: string;
    email: string;
    roles: { id: string; name: string }[];
    }

AccountRegistration
~~~~~~~~~~~~~~~~~~~
Kod::

    interface AccountRegistration {
    username: string;
    firstName: string;
    lastName: string;
    email: string;
    password: string;
    confirmPassword: string;
    }


Role
~~~~
Kod::

    interface Role {
    id: string;
    name: string;
    }


Notification
------------

Notification
~~~~~~~~~~~~
Kod::

    interface Notification {
    id: string;
    message: string;
    type: NotificationType;
    }

NotificationType
~~~~~~~~~~~~~~~~
Kod::

    type NotificationType = "success" | "info" | "warning" | "danger";

Queries
-------

CampaignFilterQuery
~~~~~~~~~~~~~~~~~~~
Kod::

    export interface CampaignFilterQuery {
    campaign?: string;
    customer?: string;
    status?: boolean;
    duration?: {
        start: Date;
        end: Date;
    };
    }


Response
--------

ResponseError
~~~~~~~~~~~~~
Kod::

    interface ResponseError {
    title: ResponseErrorType;
    status: number;
    detail: string;
    errors: Map<string, string[]>;
    }


ResponseErrorType
~~~~~~~~~~~~~~~~~
Kod::

    type ResponseErrorType = "Application exception" | "Validation failed" | "Not found" | "Invalid password";

Account
-------
Kod::

    export interface Account {
    accountId: string;
    firstName: string;
    lastName: string;
    email: string;
    roles: Role[];
    active: boolean;
    }

    export interface Role {
    id: number;
    name: string;
    }


Response
--------
Kod::

    export interface Response<T> {
    errorMessage: string,
    timeGenerated: string,
    result: T
    }

    export interface ErrorResponse {
    errorMessage: string;
    timeGenerated: string;
    }

Status
------
Kod::

    export type Status = "FETCHING" | "IDLE" | "ERROR";


