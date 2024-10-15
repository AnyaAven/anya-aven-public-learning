## Django Serializers

---

Serializers in Django REST Framework are powerful tools that bridge the gap 
between complex Django models and the JSON or XML formats commonly used in APIs. 
They handle the serialization (conversion) and deserialization (parsing) of data, 
enforce validation rules, and ensure data integrity and consistency across your API endpoints.

### Types of Serializers

- Serializer Class: The base class that provides much of the functionality required 
for serialization and deserialization.

```python
from rest_framework import serializers

class ItemSerializer(serializers.Serializer):
    id = serializers.IntegerField(read_only=True)
    name = serializers.CharField(max_length=100)
    startTime = serializers.DateTimeField()
    
    def create(self, validated_data):
        return Item.objects.create(**validated_data)
    
    def update(self, instance, validated_data):
        instance.name = validated_data.get('name', instance.name)
        instance.startTime = validated_data.get('startTime', instance.startTime)
        instance.save()
        return instance
```

- ModelSerializer: A subclass of Serializer that automatically creates fields 
based on the corresponding Django model, reducing boilerplate code.

```python
from rest_framework import serializers
from myapp.models import Item

class ItemSerializer(serializers.ModelSerializer):
    class Meta:
        model = Item
        fields = '__all__'
```

### Validating Methods
There are two primary ways to add custom validation:

1. Field-Level Validation: Methods that validate individual fields.
2. Object-Level Validation: Methods that validate the entire object or interdependent fields.

Method Naming Convention:

`validate_<fieldname>(self, value)`

Purpose: This method is automatically invoked by DRF to perform validation on a 
specific field named `<fieldname>`.
Naming Requirement: The method name must exactly match validate_ followed by the field name. 
This is a convention that DRF relies on to hook into the validation process.

