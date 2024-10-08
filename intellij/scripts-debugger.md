# Setting up scripts or debugger


# Running Docker Container locally to debug
If you are running muliple containers you may want to reverse engineer
the `docker-compose.yaml` file to run the configs locally.
This will allow you to have more control over the debugger.

Setup a script to run the same env as the container.
Using docker-compose.yml was able to mimic the same setup as the image / container.

- Set up a python template script.
- Select the python version you are using
- Set up Script as: manage.py (Django app)
- Script params as: runserver 0.0.0.0:8000
- Setup user env vars as set up in docker-compose.yml file
- Change the values of the env vars to be localhost, which will exchange the docker names.
- For example: `DATABASE_URL=postgres://postgres@localhost:5433/postgres;DEBUG=False;ES_URL=http://localhost:9200;PYTHONUNBUFFERED=1;REDIS_URL=redis://localhost:6379`

Needed to install GDAL as this was dependency for the container.
`raise ImproperlyConfigured(django.core.exceptions.ImproperlyConfigured: Could not find the GDAL library (tried "gdal", "GDAL", "gdal3.2.0", "gdal3.1.0", "gdal3.0.0", "gdal2.4.0", "gdal2.3.0", "gdal2.2.0", "gdal2.1.0", "gdal2.0.0"). Is GDAL installed? If it is, try setting GDAL_LIBRARY_PATH in your settings.`

Unsure if it was possible to install inside of my virtual environment.
I installed it locally to my machine using brew install.

Debugging JS:
- Make a JS Debug script.
  Ensure JavaScript Debugger is Configured:

* Go to Run -> Edit Configurations.
* Click the + button and select JavaScript Debug or Chrome Remote Debugging.
* Set the URL to match the page where the JSX files are being loaded.
* The configuration should point to localhost:8000 or wherever the Django development server is serving your frontend.
* Select ensure breakpoints are set

Ready to debug JSX!