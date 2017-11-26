==============================
DIAFO :: Django Dynamic Form
==============================

Diafo is a simple Django app to create dynamic form. One can add question to a form during runtime.

Detailed documentation is in the "docs" directory.

Quick start
-----------

1. Add "diafo" to your INSTALLED_APPS setting like this::

    INSTALLED_APPS = [
        ...
        'diafo',
    ]

2. Include the polls URLconf in your project urls.py like this::

    url(r'^diafo/', include('diafo.urls')),

3. Run `python manage.py migrate` to create the polls models.

4. Start the development server and visit http://127.0.0.1:8000/admin/
   to use diafo (you'll need the Admin app enabled).

5. Visit http://127.0.0.1:8000/polls/ to participate in the poll.


Bugs
----

Really? Oh well... Please Report. Or better, fix :)

