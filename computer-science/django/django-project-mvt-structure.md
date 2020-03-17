# Django Project MVT Structure

source: [https://www.geeksforgeeks.org/django-project-mvt-structure/](https://www.geeksforgeeks.org/django-project-mvt-structure/)

Django is based on **MVT \(Model-View-Template\)** architecture. MVT is a software design pattern for developing a web application. 

**MVT Structure has the following three parts –** 

**Model:** Model is going to act as the interface of your data. It is responsible for maintaining data. It is the logical data structure behind the entire application and is represented by a database \(generally relational databases such as MySql, Postgres\). To check more, visit – [Django Models](https://www.geeksforgeeks.org/django-models/)  
  


**View:** The View is the user interface — what you see in your browser when you render a website. It is represented by HTML/CSS/Javascript and Jinja files. To check more, visit – [Django Views](https://www.geeksforgeeks.org/views-in-django-python/).

**Template:** A template consists of static parts of the desired HTML output as well as some special syntax describing how dynamic content will be inserted. To check more, visit – [Django Templates](https://www.geeksforgeeks.org/django-templates/)

#### Project Structure : 

A Django Project when initialised contains basic files by default such as manage.py, view.py, etc. A simple project structure is enough to create a single page application. Here are the major files and there explanations. Inside the geeks\_site folder \( project folder \) there will be following files-

![](https://media.geeksforgeeks.org/wp-content/uploads/Screenshot-77.png)  
**manage.py-**This file is used to interact with your project via the command line\(start the server, sync the database… etc\). For getting the full list of command that can be executed by manage.py type this code in the command window-

```text
$ python manage.py help
```

   
**folder \( geeks\_site \) –** This folder contains all the packages of your project. Initially it contains four files –  
![](https://media.geeksforgeeks.org/wp-content/uploads/Screenshot-78.png)

* **\_init\_.py –** It is python package.
* **settings.py –** As the name indicates it contains all the website settings. In this file we register any applications we create, the location of our static files, database configuration details, etc.
* **urls.py –** In this file we store all links of the project and functions to call. 
* **wsgi.py –** This file is used in deploying the project in WSGI. It is used to help your Django application communicate with the web server.

### Recommended Posts:

* [How to Create a Basic Project using MVT in Django ?](https://www.geeksforgeeks.org/how-to-create-a-basic-project-using-mvt-in-django/)
* [Django Introduction \| Set 2 \(Creating a Project\)](https://www.geeksforgeeks.org/django-introduction-set-2-creating-a-project/)
* [How to Create an App in Django ?](https://www.geeksforgeeks.org/how-to-create-an-app-in-django/)
* [Django Templates \| Set - 1](https://www.geeksforgeeks.org/django-templates-set-1/)
* [Django Forms](https://www.geeksforgeeks.org/django-forms/)
* [Django Templates \| Set - 2](https://www.geeksforgeeks.org/django-templates-set-2/)
* [Django Formsets](https://www.geeksforgeeks.org/django-formsets/)
* [url - Django Template Tag](https://www.geeksforgeeks.org/url-django-template-tag/)
* [Django ModelFormSets](https://www.geeksforgeeks.org/django-modelformsets/)
* [Django Models \| Set - 1](https://www.geeksforgeeks.org/django-models-set-1/)
* [Django Templates](https://www.geeksforgeeks.org/django-templates/)
* [Django Models \| Set - 2](https://www.geeksforgeeks.org/django-models-set-2/)
* [Django Basics](https://www.geeksforgeeks.org/django-basics/)
* [Django Models](https://www.geeksforgeeks.org/django-models/)
* [Django Tutorial](https://www.geeksforgeeks.org/django-tutorial/)

![](https://media.geeksforgeeks.org/auth/profile/ebjtznuc6zybp4coauar)[**NaveenArora**](https://auth.geeksforgeeks.org/user/NaveenArora/articles)Check out this Author's [contributed articles](https://auth.geeksforgeeks.org/user/NaveenArora/articles).

If you like GeeksforGeeks and would like to contribute, you can also write an article using [contribute.geeksforgeeks.org](https://contribute.geeksforgeeks.org/) or mail your article to contribute@geeksforgeeks.org. See your article appearing on the GeeksforGeeks main page and help other Geeks.

Please Improve this article if you find anything incorrect by clicking on the "Improve Article" button below.  
  
**Improved By :** [NaveenArora](https://auth.geeksforgeeks.org/user/NaveenArora/)  


