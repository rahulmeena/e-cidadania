Configuration
=============

The e-cidadania platform is almost ready-to-use adter unpacking, but you will have
to edit the `settings.py` file.

Database
--------

**Configuring the database**::

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': 'db/sqlite.db',
            'USER': '',
            'PASSWORD': '',
            'HOST': '',
            'PORT': '',
        }
    }
    
First of all will be to set up the database. By default e-cidadania is set up to
use a local SQLite3 database, which will be useful if tested before putting the platform in production,
but that should change as soon as you finish the tests.

An example of a database on DreamHost shared server is this::

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'ecidadania_database',
            'USER': 'databaseadmin',
            'PASSWORD': 'somepassword',
            'HOST': 'mysql.ecidadania.org',
            'PORT': '',
        }
    }

Debug Mode
----------

The debug mode is enabled by default and is strongly recommended
disable to start using e-cidadania in production. For this one
must disable it in the `settings.py`::

    DEBUG = False

User Profile
------------

*ACCOUNT_ACTIVATION_DAYS* (number)

    This variable specifies how many days does the user have to activate its
    account from which it receives the confirmation email.

*GOOGLE_MAPS_API_KEY* (hash)

    API key to use Google Maps interface. You
    must create one itself though e-cidadania comes with a set,
    because it only works in the domain that you specify.

e-mail
------

*ADMINS* (list)

    List of administrators and email accounts for error reporting server. It only works if DEBUG = False
    
*EMAIL_HOST* (server)

    Email Server from which you send emails to users.
    
*DEFAULT_FROM_EMAIL*

    Default address from which emails are sent if not specified.

Language
--------

*LANGUAGE_CODE* (language code)

    Language with which to run django by default.

After settings.py
-----------------

After setting up e-cidadania to your taste, you have to run a series
command so that everything is in order.

* Create the BDD *

To create the database with the first admin user run
from the root of the project ::

. / manage.py syncdb

Create tables in the database and then ask us if we want to
create an administrative user. Choose the option that suits us
and continue.

In principle this is enough. If for some reason you want to get September 1
previous data, you must do so through methods that Django offers
but that falls outside of this manual.

* Collect static files *

e-cidadania is configured to serve static files in both
development and production, but in the latter have to *collect them* and
join them into a directory.

This directory is preset as "static", and static files
e-cidadania themselves are stored in "static_files". To collect
files you execute the command ::

. / manage.py collectstatic

After running it you can delete the directory * static_files * if you want, but
recommend to keep it in case someday you need to run the server
development.

Plugins
-------

.. note:: This section is not writing.
