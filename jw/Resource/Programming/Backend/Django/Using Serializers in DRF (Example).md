## Serializer

```python
# <app-directory>/models.py

from django.db import models

class MenuItem(models.Model):
	title = models.CharField(max_length=255)
	price = models.DecimalField(max_digits=6, decimal_places=2)
	inventory = models.SmallIntegerField()
	
```

```python
# <app-directory>/serializers.py

from rest_framework import serializers

class MenuItemSerializer(serializers.Serializer):
	id = serializers.IntegerField()
	title = serializers.CharField(max_length=255)
	price = serializers.DecimalField(max_digits=6, decimal_places=2)
	inventory = serializers.IntegerField()
	
```

```python
# <app-directory>/views.py

from rest_framework.response import Response
from rest_framework.decorators import api_view
from .models import MenuItem
from .serializers import MenuItemSerializer

@api_view()
def menu_items(requests):
	items = MenuItem.objects.all()
	serialized_items = MenuItemSerializer(items, many=True)
	return Response(serialized_items.data)

@api_view()
def single_item(request, id):
	item = MenuItem.objects.get(pk=id)
	serialized_item = MenuItemSerializer(item)
	return Response(serialized_item.data)

```

```python
# <app-directory>/urls.py

from django.urls import path
from . import views

urlpatterns = [
	path('menu-items/', view.menu_items),
	paht('menu-items/<int:pk>', view.single_item),
]
```

## Model serializers
Allow us to write less code and easily convert Django model instances to JSON object.

```python
# <app-directory>/serializers.py

from rest_framework import serializers
from .models import MenuItem
from decimal import Decimal


class MenuItemSerializer(serializers.ModelSerializer):
	stock = serializers.IntegerField(source='inventory')
	price_after_tax = serializers.SerializerMethodField(
		method_name='calculate_tax'
	)
	
	class Meta:
		model = MenuItem
		fields = ['id', 'title', 'price', 'stock']

	def calculate_tax(self, product: MenuItem):
		return product.price * Decimal(1.1)
```

## Relationship serializers
- How to use the relationship serializer to display related data in API output

```python 
# <app-directory>/models.py

from django.db import models


class Category(models.Model):
	slug = models.SlugField()
	title = models.CharField(max_length=255)

	def __str__(self):
		retirm self.title
	

class MenuItem(models.Model):
	title = models.CharField(max_length=255)
	price = models.DecimalField(max_digits=6, decimal_places=2)
	inventory = models.SmallIntegerField()
	category = models.ForeignKey(Category, on_delete=models.PROTECT, default=1)
	# Category cannot be deleted before all the menu items are deleted first.
```

```python
# <app-directory>/serializers.py

from rest_framework import serializers
from decimal import Decimal
from .models import MenuItem, Category


class CategorySerializer(serializers.ModelSerializer):
	class Meta:
		model = Category
		fields = ['id', 'slug', 'title']


class MenuItemSerializer(serializers.ModelSerializer):
	stock = serializers.Integerfield(source='inventory')
	# category = serializers.StringRelatedField()
	category = CategorySerializer()

	class Meta:
		model = MenuItem
		fields = ['id', 'title', 'price', 'stock', 'category']
		 
```

```python
# <app-directory>/views.py

from django.shortcuts import get_object_or_404
from rest_framework.response import Response
from rest_framework.decorators import api_view
from .models import MenuItem
from .serializers import MenuItemSerializer

@api_view()
def menu_items(request):
	items = MenuItem.objects.select_related('category').all()
	serialized_items = MenuItemSerializer(items, many=True)
	return Response(serialized_item.data)


```

For more serializers go to: [[Related Serializers in DRF]]