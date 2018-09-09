# Django Documentation
This repository will contain a documentation of my learnings in Django

Django is a web framework that helps develop web applications easily. 
Django follows MVT (Model View Template) pattern, which is similar to MVC (Model View Controller), just that the controller's job is done by the Django framework itself.

A Django Project Consists of the following:-

## 1. Models: 
#### The Models are Class representation of Database Tables. 
Say, a table `Student` in DB with columns:
  
  i. `id` 
  ii. `name`
  iii. `dob`
  iv. `address`

Will be represented as follows in the django models.

```
class Student(models.Model):
    id      = models.AutoField(primary_key=True)
    name    = models.CharField(max_length=200)
    dob     = models.DateTimeField(blank=True, null=True)
    address = models.TextField()
   
```
Django takes care of the table creation, the maintenance of data models and everything.
The Django ORM  gives us the a flexible and pythonic way to query the databases. 
Examples:-
1. To Query a table:-
    `Student.objects.all()` : Gives us all the entries of the Student model.
    
2. To Filter a table entries based on a field:- 
    `Student.objects.get(name='Prince Manohar')` : Gives all the Student entries which have `name` value as `'Prince Manohar'`

## 2. Views: 
#### Views contains our business logic where we write, what data we want to send in the response of an API and in what format
A View is a function in the `views.py`. Views interact with the Models and bring the data, and puts them into the Templates to render them as the right formats.  

## 3. Templates: 
#### Templates are like files with html and/or some python code in it. 
Templates help us create dynamic html tags with data. Django Templating Engine supports python like code in Templates which helps us add logic to how the templte should render with our data.
Example:- https://tutorial.djangogirls.org/en/django_templates/

## 4. URLs - urls.py
#### Which url should go to which view, is configured in urls.py
The url configuration is like a mapping, where we specify how django will hanle a request, based on which url endpoint was hit.

See https://tutorial.djangogirls.org/en/django_urls/ for more details.


# Setting Up Django Project and make a web application Step by Step:-

### 1. Setup a project `myproj` 

`django-admin.py startproject myproj .`

### 2. Configure db in `settings.py`

### 3. Apply above configurations and create DB in Database as per step 2. 

`python manage.py migrate`

### 4. Running the Server

`python manage.py runserver`

### 5. Create your application `myapp1`

`python manage.py startapp myapp1`

This is like one of the many web applications we want to create in the current project.

Add `myapp1` entry to the `INSTALLED_APPS` of settings.py

# Make and Apply Migrations
Whenever have created new Models in the models.py or edit the existing Models, we need to tell the database about the changes. 
For this we use the following 2 commands:-

#### Step 1: 
`python manage.py makemigrations` : This command reads the models.py and puts specific instructions on what to create or change in the database in the `migrations`folder. 

#### Step 2: 
`python manage.py migrate` : This command will actually talk to the databse and apply all the migrations as per Step 1. All the tables will be created/updated.


