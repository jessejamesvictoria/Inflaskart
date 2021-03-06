Inflaskart
==========

'Inflaskart' is a demo of a clone of Instacart implemented using Django,
ie. it is an online grocery shopping web application.

The display is implemented using HTML5/CSS3 and Bootstrap.
A postgreSQL database is used to store the model instances.
It needs to be PostgreSQL >= 9.4 to support the jsonb type used in Django's
JSONField (which is used in the Order model).

More about Django web framework: https://docs.djangoproject.com/en/1.10/


Repository content
------------------
+ manage.py: implements the Django command-line utility for administrative tasks

+ inflaskart = the Django project package containing the following:
    - __init__.py
    - settings.py
    - urls.py
    - wsgi.py
    - a static directory containing the favicon

+ grocerystore = the Django app package containing the following:
    - __init__.py
    - admin.py
    - apps.py
    - forms.py
    - models.py
    - tests.py
    - urls.py
    - views.py
    - zipcodes_list.txt = a list of the available zip codes areas to shop in
    - a migrations folder (containing only __init__.py)
    - a templates folder
    - a static folder (containing a style sheet, the logo, and the resume to download)

+ requirements.txt


How does it work
----------------
In order to be able to set up Inflaskart (locally), you need to:

1. Clone this repository

2. Open the terminal and navigate to this repository. You can install the required
modules/applications using the following command (you need to have pip installed):
    ```sh
    pip install -r requirements.txt
    ```
NB: it's best practice to do this step in a virtual environment

3. Have PostgreSQL installed and running locally. You need to have an existing
database called 'grocerystore_db' (if you want to use a different database name,
you need to set DATABASE['NAME'] to the name you want in settings.py)

4. Create your database tables based on the application models (NB: here the
application mane is 'grocerystore')
In order to do that, in the terminal navigate to the cloned repository and
create your database migrations:
    ```sh
    python manage.py makemigrations application_name
    ```
Then run the following command to apply the migrations to the database:
    ```sh
    python manage.py migrate
    ```

5. Still in the terminal and in the cloned repository, you can run the project
server by typing in the following command:
    ```sh
    python manage.py runserver
    ```
By default, the server will run locally on port 8000.
Now you can access the index page of your web app (app called 'grocerystore') in
your browser with the following URL:
'localhost:8000/grocerystore/‘

6. In order to be able to create products and stores instances to play with this
application, you need to create an admin/superuser profile:
    ```sh
    python manage.py createsuperuser
    ```
Then you will be prompted for your email address and password.
More info here: https://docs.djangoproject.com/en/1.10/intro/tutorial02/#introducing-the-django-admin

7. You can access the admin page in your browser by typing in the following URL:
'localhost:8000/admin/‘
The more stores, products and availabilities you create, the better!

8. Then access the Inflaskart index page in your browser on
'localhost:8000/grocerystore/‘, and have fun!


How to run the tests
--------------------
In the command line, navigate to the project directory (not the app one), then
enter the following command:
  ```sh
  python manage.py test
  ```

Features
--------
The user can create an account and then log in/out.

Though it is possible to navigate in the application anonymously (ie. without
being logged in or registered), the user must create an account and be logged in
to be able to place an order.

The user can shop in different stores, including stores that don't deliver their
address. In that case, they are notified that they need to pick up their order
instead of getting it delivered.

It is not possible to buy more than 20 items of the same product.
There's no delivery fee if the order total amount is $20 or more; otherwise there's
a $3 fee for delivery.
The user has access to his/her order history.

An ID is required upon delivery of alcoholic beverages.


Room for improvement
--------------------
This project is still WIP:
- need to implement a way to verify a user's email address;
- need to implement a way to allow the user to check their password when signing
up (ie: entering it twice);
- need to implement a way to allow the user to change their password;
- in real life, need to implement a way to store the user's credit card information
securely and properly implement the checkout process;
- in real life, a sales tax API might be needed to automatically calculate applicable taxes
