# Represent

[![Dependency Status](https://gemnasium.com/opennorth/represent-canada.png)](https://gemnasium.com/opennorth/represent-canada)

[Represent](https://represent.opennorth.ca) is the open database of Canadian elected officials and electoral districts. It provides a [REST API](https://represent.opennorth.ca/api/) to boundary, representative, and postcode resources.

This repository contains a master Django project, documentation, and a demo app. Code for the individual components of the API is in separate packages, which this project depends on:

* [represent-boundaries](https://github.com/opennorth/represent-boundaries)
* [represent-reps](https://github.com/opennorth/represent-reps)
* [represent-postcodes](https://github.com/opennorth/represent-postcodes)

There's also a package to provide colourful district map tiles:

* [represent-maps](https://github.com/tauberer/represent-maps)

## Getting Started

The following instructions are to setup your own instance of Represent. If you just want access to data, [please read our API documentation](https://represent.opennorth.ca/api/).

Follow the instructions in the [Python Quick Start Guide](https://github.com/opennorth/wiki/wiki/Python-Quick-Start%3A-OS-X) to install Homebrew, Git, Python, virtualenv, GDAL and PostGIS. The [deployment](deployment/) uses Python 3.5, PostgreSQL 9.6, and PostGIS 2.3.

Create a database and enable PostGIS (commands should be issued as user `postgres`):

    createdb represent
    psql -c "CREATE EXTENSION postgis;" represent

Install the project:

    pyvenv represent-env
    source represent-env/bin/activate
    git clone https://github.com/imhangoo/represent-canada.git
    cd represent-canada
    pip install -r requirements.txt

Configure the `DATABASES` Django setting and and create the database tables:

    cp represent/settings.py.example represent/settings.py
    $EDITOR represent/settings.py
    python manage.py migrate

You can launch a development server with:

    python manage.py runserver

## Adding Data

[Download the data](https://github.com/opennorth/represent-canada-data), and then symlink `represent-canada-data` into the project directory:

    mkdir data
    ln -s /path/to/represent-canada-data/ data/shapefiles

To load the data into the API, see the boundaries, representatives, and postcodes packages.

## Maintenance

Read the [wiki](https://github.com/opennorth/represent-canada/wiki) and [deployment/](deployment/).

## Bugs? Questions?

This repository is on GitHub: [https://github.com/opennorth/represent-canada](https://github.com/opennorth/represent-canada), where your contributions, forks, bug reports, feature requests, and feedback are greatly welcomed.

Copyright (c) 2017 Open North Inc., released under the MIT license
