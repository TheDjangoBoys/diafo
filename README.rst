==============================
DIAFO :: Django Dynamic Form
==============================

Diafo is a simple Django app to create dynamic form. One can add question to a form during runtime.

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

    pip install django-filter

2. Then add ``'django_filters'`` to your ``INSTALLED_APPS``.

.. code-block:: python

    INSTALLED_APPS = [
        ...
        'django_filters',
    ]
3. Include the polls URLconf in your project urls.py like this::

    url(r'^diafo/', include('diafo.urls')),

4.  Run `python manage.py migrate` to create the diafo models.



Usage
-----

Django-filter can be used for generating interfaces similar to the Django
admin's ``list_filter`` interface.  It has an API very similar to Django's
``ModelForms``.  For example, if you had a Product model you could have a
filterset for it with the code:

.. code-block:: python

    import django_filters

    class ProductFilter(django_filters.FilterSet):
        class Meta:
            model = Product
            fields = ['name', 'price', 'manufacturer']


And then in your view you could do:

.. code-block:: python

    def product_list(request):
        filter = ProductFilter(request.GET, queryset=Product.objects.all())
        return render(request, 'my_app/template.html', {'filter': filter})


Usage with Django REST Framework
--------------------------------

Django-filter provides a custom ``FilterSet`` and filter backend for use with
Django REST Framework.

To use this adjust your import to use
``django_filters.rest_framework.FilterSet``.

.. code-block:: python

    from django_filters import rest_framework as filters

    class ProductFilter(filters.FilterSet):
        class Meta:
            model = Product
            fields = ('category', 'in_stock')


For more details see the `DRF integration docs`_.


Support
-------

If you have questions about usage or development you can contact me.

Bugs
----

Really? Oh well... Please Report. Or better, fix :)
