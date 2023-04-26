# Create a REST API using Django Rest Framework II

## Topics covered

Token Authentication, pagination and related ModelViewSets.

## Goal achieved

You will make your RESTful API ready for production by using Token Authentication instead of Basic Authentication.

You will add pagination to the list of items and add an endpoint for the employees including the related fields.

## Steps

### Using Token Authentication

If you followed Django REST Framework's quick start tutorial you may have included the following line in your `ModelViewSets` (if you didn't, do it now):

```
permission_classes = [permissions.IsAuthenticated]
```

This restricts the view to validated users and uses **Basic Authentication** to figure if each request is authorized to use this API endpoint. As you know, this is not recommended for production environments.

> The APi can be used with Postman or curl by passing the username and password on every request.
>
> This is the standard username and password of a user. If a developer uses these credentials to work with the API and the user changes its password, the developer's application will stop working.

To publish the API in production, you must first change the validation to a Token Authentication based system.

Follow the guidelines at [https://www.django-rest-framework.org/api-guide/authentication/](https://www.django-rest-framework.org/api-guide/authentication/) to do so.

Confirm it works by using Postman or Curl. In Postman, you may have to manually add a header named `Authorization` and the value `Token <YOUR_TOKEN_HERE>`.

### Paginating the item list

You may have noticed the [http://localhost:8000/stock/api/items/](http://localhost:8000/stock/api/items/) endpoint takes a little. This is not optimal and it may be better to paginate all the view sets by default.

Limit the number of elements in a page to 100. Then, explore the endpoint to confirm it works.

### Adding Employee CRUD to the API

Finally, add the Employee model to the REST API following these guidelines:

- Show a key named `user` that will have a string with the `user.username` of each employee.
- Show a key named `lead_by` that will have a string with the API link of the leader of each employee.
- Show a key named `workinghours` that will be a list of strings indicating the day of the week, start time and end time.
- Show a key named `edits` as a list of serialized `EditedItems` objects. Each object will have a key `item` (as a serialized `Item` object) and a key `date` with the date of the edition as a string.

**Sample:** http://localhost:8000/stock/api/employees/
```
{
    "count": 10,
    "next": null,
    "previous": null,
    "results": [
        {
            "user": "Juno",
            "lead_by": "http://localhost:8000/stock/api/employees/7/",
            "workinghours": [
                "Monday. From 09:00:00 to 14:00:00.",
                "Tuesday. From 10:00:00 to 14:00:00.",
                "Wednesday. From 09:00:00 to 14:00:00.",
                "Thursday. From 09:00:00 to 14:00:00.",
                "Friday. From 09:00:00 to 14:00:00."
            ],
            "edits": [
                {
                    "item": {
                        "name": "Super cool smartphone!",
                        "state": "Almost new",
                        "category": "Smartphone",
                        "warehouse": "Warehouse 1",
                        "dimensions": null,
                        "date_of_stock": "2020-10-16T01:12:04Z",
                        "picture": null
                    },
                    "date": "2021-12-24T13:27:32.248772Z"
                }
            ],
        }
    ]
}
```
