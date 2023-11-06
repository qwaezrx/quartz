[[Django]] 
### 1. `mkdir <root-name>`
### 2. `cd <root-name>`
### 3. `django-admin startproject <project-name> .`
### 4. `pipenv shell`
### 5. Update the `Pipfile` with following text.
```
[[source]]

url = "https://pypi.org/simple"

verify_ssl = true

name = "pypi"

[packages]

django = "*"

djangorestframework = "*"

djangorestframework-xml = "*"

djoser = "*"

[dev-packages]

[requires]

python_version = "3.9"	
```
### 6.  `pipenv install`
### 7.  `python3 manage.py startapp <app-name>`
### 8. `python3 manage.py runserver`
### 9. Create `urls.py` file in the app-level directory. and paste the following code inside it.
```python
from django.urls import path
from . import views

urlpatterns = [
	path('ratings', views.RatingsView.as_view()),
]
```
> [!NOTE]
> The specific url configurations will differ according to the view created
### 10. Open the `urls.py` file in the project-level directory and update the code as follow:
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
	path('admin/', admin.site.urls),
	path('api/', include('<app-name>.urls')),
]
```
> [!NOTE]
> The specific url configuration at the project-level will vary according to the name of the app
