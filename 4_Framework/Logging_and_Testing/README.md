# Django Logging & Testing

## Topics covered

* Django logging.
* Unit tests for endpoints, views and forms.

## Goals
Using the Django project you created for [Django MVC, ORM and Forms](../MVC_ORM_&_Forms):
* You will define a policy using Django's logging feature to store in the file system messages about various events.
* You will add automated tests to your Django project to make sure all endpoints, views and forms work as expected.

## Tasks
### Task 1

Define a logger named `orders.log` that will store all information related to events happening when a user places an order.

This logger should use a handler that stores the messages in a file on the `logs` directory of the Django project root directory.

Once you defined the logger policy in the project.settings, edit the view to send messages to the log every time someone orders an item. The message should show the name of the item, the amount and the date.

Define another logger named `404s.log` to record every 404 error. To do so, you can define a path to catch anything that does not match any previous path. On the associated view, you can show a customized error and send a message to the log with the URL that produced the `404. Not found` error.


### Task 2

Define tests for your endpoints.

Because we don't actually want the tests to interfere with the real data, define a `setUpClass` method in your `TestCase` to backup a copy of the original file. Once all the tests are done, you can restore the backup using the `tearDownClass` method.

This way, you can test the placing of the orders without actually touching the real data.

Some of the tests you can perform are:

**Testing the path resolutions**

Assert that each of the paths resolves correctly with a 200 status code.

> HINT: use the `django.test.Client` class.

**Testing the TemplateViews**

Assert that the `get_context_data` method of each view extending the built-in TemplateView returns the expected context.

You can check for the presence of specific keys in the context dictionary, but you can also check the type of each value and in some cases the value or the length of the value.

> HINT: import the views in the `tests.py` file and instantiate them manually to call the `get_context_data` and examine the return.

**Testing the FormViews**

Create demo POST requests to the `stock:search` and `stock:item-order` paths.

Confirm that the response is an `HttpResponseRedirect` object with a status_code of `302`.

Then, confirm that the page they are redirecting to is the appropriate one.

> HINT: use the `follow` argument and the `redirect_chain` property.

For the placing of orders, confirm that after executing a POST request, the item actually gets removed from the stock (search the item and count the amount before and after the request).

