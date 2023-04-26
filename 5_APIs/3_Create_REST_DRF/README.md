# Create a REST API using Django Rest Framework

## Topics covered

Django REST Framework. Serializers and ModelViewSets.

## Goal achieved

You will create a RESTful API to allow third applications to create, read, update and delete items in stock.

## Description

After going through the corresponding lecture and reading Django REST Framework's [quick start documentation](https://www.django-rest-framework.org/tutorial/quickstart/) create a RESTful API for your stock models (items and warehouses) using the following guidelines:

- Define your API root at `/stock/api/`.
- Use the `ModelViewSet` class from Django REST Framework to provide access to all CRUD operations on both the `Item` and the `Warehouse` models.
- Show the warehouse field in the `Item` model as a string with the name of the warehouse.

Once you have it running, explore it in your browser at [http://localhost:8000/stock/api/items/](http://localhost:8000/stock/api/items/).
