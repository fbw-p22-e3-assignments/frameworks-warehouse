# Google Cloud Platform

## Topics covered

Cloud SQL, App Engine and general deployment of a Django website on the Google Cloud Platform.

## Goal achieved

You will make your project website public on the Internet.

## Description

Using what you learned during the lecture and the tutorial at https://cloud.google.com/python/django/run#gcloud_3 deploy your website to the Google Cloud Platform.

You can follow the tutorial almost to the step, with the difference that you will not be deploying the sample app provided in the tutorial. So instead of cloning that app, check the key changes (on the section **Understand the code**) and apply them to your Django project.

Before starting, dump all the data into Django fixtures, so you can migrate the data as well as the app. *Don't migrate the entire `auth` app as it may be conflicting with the data initially created by Django. Instead, export only the `auth.user` model.*

When, at the end, you execute the instruction to deploy the app, you may get the following message in the terminal window:

> ERROR: (gcloud.app.deploy) NOT_FOUND: Unable to retrieve P4SA: [service-379790524512@gcp-gae-service.iam.gserviceaccount.com] from GAIA. Could be GAIA propagation delay or request from deleted apps.

Try executing the same instruction again. This [has been reported](https://stackoverflow.com/a/67057390/4477659) in various occasions as a *solution* to this error.

Once the deployment works correctly, visit the new website. If you get any error, redirect all the Django logging handlers in your `settings.py` to the console (StreamHandler) and use the Google Cloud logs to see what the error is.

```
gcloud app logs tail -s default
```
