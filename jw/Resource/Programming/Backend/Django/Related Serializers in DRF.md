[[DRF]]
[[Django]]
## Introduction
This page has some interesting tips and tricks regarding serialization, like how to automatically display a nesting model field using the depth option of the serializer. You will also learn how to display related model fields as [[hyperlink]]s by using `HyperlinkedRelatedField` or by using a new type of serializer called the `HyperlinkedModelSerializer`.

> [!NOTE]
> The code for this page builds on [[Using Serializers in DRF (Example)]]

---

## Nested fields
If you visit `menu-items` endpoint, you would note the category displays as a nested field with its id, title, and slug.

> `GET /api/menu-items`

```json
[
	{
		"id": 1,
		"title": "Butter Scotch Icecream",
		"price": "3.3",
		"stock": 100,
		"price_after_tax": 3.45,
		"category": {
			"id": 1,
			"slug": "icecream",
			"title": "Icecream"
		}
	}
]
```

This can be achieved in 2 ways.
### Method 1
The first way to do this is to create a category serializer in `serializer.py` and include it in the menu item serializer
```python
from rest_framework import serializers
from .models import Category, MenuItem
from decimal import Decimal


class CategorySerializer(serializers.ModelSerializer):
	class Meta:
		model = Category
		fields = ['id', 'slug', 'title']


class MenuItemSerializer(serailizers.ModelSerializer):
	stock = serializers.IntegerField(source='inventory')
	price_after_tax = serializers.SerializerMethodField(
		method_name='calculate_tax'
	)
	category = CategorySerializer()
	
	class Meta:
		model = MenuItem
		fields = ['id', 'title', 'price', 'stock', 'price_after_tax', 'category']

	def calculate_tax(self, product: MenuItem):
		return product.price * Decimal(1.1)
```

### Method 2
Instead of declaring the category field as `CategorySerializer`, you can specify that `depth=1` is in the Meta class in `MenuItemSerializer`. This way, all relationships in this serializer will display every field related to that model.
```python

class MenuItemSerializer(serializers.ModelSerializer):
	stock = serializers.IntegerField(souce='inventory')
	price_after_tax = serializers.SerializerMethodField(
		method_name='calculate_tax'
	)
	class Meta:
		model = MenuItem
		fields = ['id', 'title', 'price', 'stock', 'price_after_tax', 'category']
		
		depth = 1
		# All relationships in this serializer will 
		# display every field related to that model
	def calculate_tax(self, product: MenuItem):
		return product.price * Decimal(1.1)

```

---

## Display a related model fields as a hyperlink
In DRF you can display every related model field as a hyperlink in the API output. Like this:
`http://127.0.0.1:8000/api/category/{categoryId}` for the category field. There are 2 ways to do this.

> `GET /api/menu-items`

```json
[
	{
		"id": 1,
		"title": "Butter Scotch Icecream",
		"price": "3.3",
		"stock": 100,
		"price_after_tax": 3.45,
		"category": "http://127.0.0.1:8000/api/category/1"
	}
]
```
### Method 1: HyperlinkedRelatedField


1. <u>Create and map a new view function</u>
	
	Every `HyperlinkedRelatedField` field in a serializer needs a `queryset` to find the related object and a view name that is used to map the hyperlinked URL pattern.

	Thus you have to create a new function in the `views.py` file that will handle the `categoryId` endpoints.
	```python
	from rest_framework.decorators import api_view
	from .models import Category
	from .serializers import CategorySerializer
	
	@api_view()
	def category_detail(request, pk):
		category = get_object_or_404(Category, pk=pk)
		serialized_category = CategorySerializer(category)
		return Response(serialized_category.data)
		
	``` 
	 
	 Then you map this function in the `urls.py` file with a view name.
	```python
	path('category/<int:pk>', views.category_detail, name='category-detail')
	```
	
	> [!Tip]
	>There is a convention you must follow. The rule is that you have to add `-detail` after the related field name. This is why the view name was `category-detail` in this code.


1. <u>Create a HyperLinkedRelatedField in the serializer</u>
	
	The next step is to change the `MenuItemSerializer` code.
	
	```python
	from .models import Category
	
	class MenuItemSerializer(serializers.ModelSerializer):
		# ...
		category = serializers.HyperlinkedRelatedField(
			queryset=Category.objects.all(),
			view_name='category-detail' # You can remove this line since the field name follows the convention.
		)
		# ...
	```
	
	Note how `queryset` and a view name are provided in the category `HyperlinkedRelatedField`.

3. <u>Add context</u>
	
	The final step is to add context to the `MenuItemSerializer` in the `menu_items` function, as below.
	```python
	serialized_item = MenuItemSerializer(items, many=True, context={'request': request})
	```
	
	> [!Note]
	> The argument `context={'request': request}` lets the `menu-tems` endpoint display the category field as a hyperlink.


### Method 2: HyperlinkedModelSerializer
Another way, you need to change the code in `serializers.py` so that the `MenuItemSerializer` extends the `serializers.HyperlinkedModelSerializer` class instead of `serializers.ModelSerializer` class.

```python
class MenuItemSerializer(serializers.HyperlinkedModelSerializer):
	...
	class Meta:
		model = MenuItem
		fields = ['id', 'title', 'price', 'stock', 'price_after_tax', 'category']
	...
```

When you use the `HyperlinkedModelSerializer`, the output of the `menu-items` endpoint produces the same as the "Method 1" but the code is much cleaner and simpler.

>[!Note]
>When you use a `HyperlinkedModelSerializer`, you still need the URL pattern with a view name as you did in "Method 1".

```python
urlpatterns = [
	path('menu-items', views.menu_items),
	path('menu_items/<int:pk>', views.single_item),
	path('category/<int:pk>', views.category_detail, name='category-detail'),
]
```
