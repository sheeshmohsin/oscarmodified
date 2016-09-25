Documentation
=============

Getting Up and Running
----------------------

The steps below will get you up and running with a local development environment. We assume you have the following installed:

* pip
* virtualenv

Clone the repository::

    $ cd ecommerce

First make sure to create and activate a virtualenv_, then open a terminal at the project root and install the requirements for local development::

    $ pip install -r requirements.txt

.. _virtualenv: http://docs.python-guide.org/en/latest/dev/virtualenvs/

Run the Django ``migrate`` command::

    $ python manage.py migrate

You can now run the usual Django ``runserver`` command::

    $ python manage.py runserver


Activate Reactjs in template
----------------------------

First you need to load the reactjs tag in each page or atleast in base html page using this command in template

    {% load reactjs %}

reactjs source file

Include the reactjs file(s) as `<scrip...></script>` tag(s).

    {% reactjs %}

Include the reactjs-with-addons file(s) as `<scrip...></script>` tag(s).

    {% reactjs_with_addons %}


Work Done for Multiple Dealers
------------------------------

All the modification are done in django oscar as mentioned in django oscar documentation for multiple dealers under this multiurl_ :

.. _multiurl: https://django-oscar.readthedocs.io/en/releases-0.6/howto/multi_dealer_setup.html


* Converted ManyToManyField to OneToOneField, For details look at url1_ 

* Enforced Creating of StockRecord with every Product, For details look at this url url2_

* When a Product is created, Stockrecord.partner gets set to self.request.user.partner (created if necessary), For details look at url3_

* It was needed to filter the dashboard to return only a list of products that belong to a dealer but ProductListView is depreceated in newer versions of django oscar as its not needed anymore with search improvements, For details look at url4_

* It was needed to replace the decorator to remove staff to login required, so i edited staff required decorator and made it similiar to login required, For details look at url5_


.. _url1: https://github.com/sheeshmohsin/django-oscar/blob/master/src/oscar/apps/partner/abstract_models.py#L30

.. _url2: https://github.com/sheeshmohsin/django-oscar/blob/master/src/oscar/apps/partner/admin.py#L24

.. _url3: https://github.com/sheeshmohsin/django-oscar/blob/master/src/oscar/apps/partner/admin.py#L14

.. _url4: https://github.com/sheeshmohsin/django-oscar/blob/c7956eb6adc315c88c780d8c28535eb3118d32f1/docs/source/releases/v0.7.rst#backwards-incompatible-changes-in-07

.. _url5: https://github.com/sheeshmohsin/django-oscar/blob/master/src/oscar/views/decorators.py#L30

