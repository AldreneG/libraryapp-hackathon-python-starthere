# Setup
To set up this project on your own machine, perform these steps.

1. Fork this repository, then clone it. Fork it via the Github website, then clone it with either Github desktop or the command line (if you've got the ssh keys set up)
```
$ git clone git@github.com:GirlsCodeMK/libraryapp-hackathon-python-starthere.git
```
2. Once you have a copy of the repository, open a terminal in that directory
```    
$ cd /path/to/libraryapp-hackathon-python-starthere/
```
3. Once there, create and activate a virtual environment for the project    
```    
$ python3 -m venv gcmk
$ source gcmk/bin/activate
```
4. Install the required libraries, such as Django    
```    
$ pip install -r requirements.txt
```
5. Check you have the correct version
```    
$ python -m django --version
2.1.4
```
6. Run a migration to create the database
```
$ python manage.py migrate
```

## Create users and records

There are two options here: either use the pre-populated sample data, or create users and data yourseelf.

### Using sample data (recommended)

After running `migrate`, pick _one_  of the datasets to include in the database.

1. User groups & permissions:
```
$ python manage.py loaddata library-auth.json
```
2. User groups & permissions, and sample users
```
$ python manage.py loaddata library-auth-user.json
```
3. User groups & permissions, sample users, and sample books & loans
```
$ python manage.py loaddata library-auth-user-library.json
```

Then run the server:
```
$ python manage.py runserver
```

and visit the library site (`127.0.0.1:8000/library`) in a web browser. The admin site is at `127.0.0.1:8000/admin` should you need it.

### Creating users and data by hand
1. Create a superuser
```
$ python manage.py createsuperuser
```
2. Run the server, and open the admin site (`127.0.0.1:8000/admin`) in a web browser
```
$ python manage.py runserver
```
3. In the admin site, create two groups: `Librarian` and `Library user`. Give them the following permissions:
    * _Librarian_
        * auth | user | Can add user
        * auth | user | Can change user
        * auth | user | Can delete user
        * auth | user | Can view user
        * library | book | Can add book
        * library | book | Can change book
        * library | book | Can delete book
        * library | book | Can view book
        * library | copy | Can add copy
        * library | copy | Can change copy
        * library | copy | Can delete copy
        * library | copy | Can view copy
        * library | loan | Can add loan
        * library | loan | Set book as on loan
        * library | loan | Set book as returned
        * library | loan | View all users' loans
        * library | loan | Can change loan
        * library | loan | Can delete loan
        * library | loan | Can view loan
    * _Library user_
        * library | book | Can view book
        * library | copy | Can view copy
        * library | loan | Can view loan
4. In the admin site, create some users, books, copies, and loans. Create at least one librarian and one library-user.

# Links

The [Django documentation](https://docs.djangoproject.com/en/2.1/) is essential reading, including the [Django "getting started" tutorial](https://docs.djangoproject.com/en/2.1/intro/).

This application is based on the [DjangoGirls tutorial systemm](https://tutorial.djangogirls.org/en/) and the [Mozilla Development tutorial](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Tutorial_local_library_website).
