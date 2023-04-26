# Consume REST APIs using Python II

## Topics covered

Using REST APIs with Python and Django to publish data.

## Goal achieved

You will add to your website a picture for every item in stock and the ability to upload new pictures and store them at [image4io](https://image4.io/).

The employees will be able to use the edit item form to upload a picture that will be stored in Image4io instead of the local file system.

## Description

First, add a new field named `picture` of type `TextField` to the `Item` model. This field will store the URL of the picture once we have uploaded it to Image4io.

If this field has a value, the image should appear on the complete list of items at [http://localhost:8000/stock/items/](http://localhost:8000/stock/items/) and in the edit item form at [http://localhost:8000/stock/items/\<pk>/](http://localhost:8000/stock/items/pk/).

On the view, change the default form widget used by this field to a `FileInput` widget, so that the form lets the user upload a file to fill this field up instead of typing the Image4io URL manually.

On submit, the edit item view should upload the file to Image4io, get the URL back and save it in the `picture` model field. If an error is produced in this process, a message should be shown to the user.

> To use Image4io you will have to create a new account, if you don't already have one, choose a *cloudname* of your choice (any unique string will do) and copy the API Key and API Secret (*you can ignore the account setup for now*).
>
> Send your requests to `https://api.image4.io/v1.0/`.
>
> Read the documentation at [https://image4.io/en/documentation/api-sdk/#operation/UploadImage](https://image4.io/en/documentation/api-sdk/#operation/UploadImage) to understand how to use the API.
