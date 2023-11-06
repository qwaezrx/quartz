

```python
from django.shortcuts import get_object_or_404
from rest_framework.decorators import api_view
from rest_framework.response import Response
from rest_framework import status
from .models import MenuItem
from .serializers import MenuItemSerializer


@api_view(['GET', 'POST'])
def menu_items(request):
	if request.method == 'GET':
		items = MenuItem.objects.select_related('category').all()
		serialized_items = MenuItemSerializer(items, many=True)
	elif request.method == 'POST':
		serialized_items = MenuItemSerializer(data=request.data)
		serialized_items.is_valid(raise_exception=True)
		# You cannot access to the record before saving it
		serialized_items.save
		return Response(serialized_items.data, status.HTTP_201_CREATED)
```

```python
# <app-directory>/serializers.py

...

class MenuItemSerializer(serializers.ModelSerializer):
	...
	category = CategorySerializer(read_only=True)
	category_id = serializers.IntegerField(write_only=True)
	class Meta:
		model = MenuItem
		fields = [..., 'category', 'category_id']
```

> [!Tip]
> Instead of making one serializer to do everything, you can create multiple serializers and use them separately in your `GET` and `POST` calls.

## Related Documents
- [[Django]]
- [[DRF]]