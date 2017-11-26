==============================
DIAFO :: Django Dynamic Form
==============================

Diafo is a simple Django app for generaing dynamic forms during the runtime. 

Detailed documentation is in the "docs" directory.


Requirements
------------

* **Python**: 3.4, 3.5, 3.6
* **Django**: 1.11, 2.0b
* **Django bootstrap form**: 1.4


Installation
------------

1. Install using pip:

.. code-block:: sh

    pip3 install diafo
    pip3 install django-bootstrap-form

2. Then add ``'django_filters'`` to your ``INSTALLED_APPS``.

.. code-block:: python

    INSTALLED_APPS = [
        ...
        'diafo',
	'bootstrapform',
    ]

3. Include the polls URLconf in your project urls.py like this::

    url(r'^diafo/', include('diafo.urls')),

4.  Run `python manage.py migrate` to create the diafo models.



Usage
-----

Diafo can be used for generating Questionnaires consisting various questions during runtime. One can specify the question type like CharField, TextFied, ChoiceField, MultipleChoiceField, etc. Requirement can also be mentioned whether the question is compulsary or not. 

Let see its usage through a simple survey webapp.

.. code-block:: python

    from diafo.models import Questionnaire

    class Survey(models.Model):
	title = models.CharField(max_length=200)
    	form = models.OneToOneField(Questionnaire, null=True)

        


And then in your view you could do:

.. code-block:: python

    def new_survey(request):
	...
	#get the title by using form or any how..
	form = Questionnaire.objects.create(name=tilte)
        survey = Survey.objects.create(title=title, form = form)
	return HttpResponseRedirect(reverse('diafo:admin_view', kwargs={'pk': survey.form.pk}))
           




Support
-------

If you have questions about usage or development you can contact me.

Bugs
----

Really? Oh well... Please Report. Or better, fix :)
