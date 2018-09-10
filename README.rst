Based on Django/Mezzanine


References:

- Mezzanine http://mezzanine.jupo.org/
- Django https://www.djangoproject.com/
- Python https://www.python.org/
 

Development Installation
=========================

The development installation process is similar to any standard Django project.

Database
--------
You will need to install prepare your database engine to be used.

By default Django supports SQLite, PostgresSQL, MySQL and Oracle as database engines.
Support for other database engines may be available via third party packages.

Unless you are using SQLite you may need to create a database and a database user in advance.


Python virtual environment
--------------------------
It it highly recommended to use Python utilities like virtualenv or virtualenvwrapper
or a similar alternative in order to work within a virtual environment for better
Python dependancies management.

For more information about usage of Python virtual environments please search
for available resources online.

Create and virtual activate a virtualenvironment for the project


Project setup
-------------

Download the source code

.. code:: bash

    git clone https://github.com/tehamalab/tanpud.git


Go to project root

.. code:: bash

    cd tanpud


make sure your python virtual environment is active then use pip to install project requirements.

.. code:: bash

    pip install -r requirements.txt


Change your project settings according to your requirements.
For example change your database setting to reflet your existing setup and enable debug mode.

.. code:: bash

    # .env file

    DEBUG = True
    DATABASE_ENGINE = ''
    DATABASE_NAME = ''


Local project setting which are not supposed to be tracked by git settings modified by

 - using system environment variables
 - using environment variables written in ``.env`` file at the project root
 - By creating a local settings file at the project root ``tanpud/local_settings.py``


Otherwise you can edit the ``tanpud/settings.py`` file directly.
For more information on available settings please consult Django and Mezzanine documentation

Check if things are ok

.. code:: bash

    python manage.py check


Create database tables

::

    python manage.py migrate


Create a superuser for administrative access

.. code:: bash

    python manage.py createsuperuser


**NOTE:** When you are executing ``python manage.py ...`` commands make sure the vertualenv is active.


Starting the development server
--------------------------------

Django comes with an inbuilt server which can be used during development.
You shouldn't be using this server on production sites.

To start the development server go to your project root directory run

.. code:: bash

    python manage.py runserver


Now you will be able to access a site locally via http://127.0.0.1:8000


Deployment
==========

Since this is a typical Django project any standard Django deployment stack can be used.
For more information on Django deployment please look for available resources on the
Internet including https://docs.djangoproject.com/en/1.11/howto/deployment/

Most Django deployments usually include a frontend web/proxy server like Nginx,
a WSGI application server  like Gunicorn or uWSGI.

In production usually you won't want Django or your application server to serve static
files directly instead you may use Nginx or another server optimized for serving
static content.

You may also want to use a process manager like "supervisor" to manage your application daemon.
