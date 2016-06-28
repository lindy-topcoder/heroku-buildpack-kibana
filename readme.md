# Heroku Buildpack for Kibana

This buildpack downloads and installs Kibana into a Heroku app slug.

## Compatibility

Tested against Kibana 5.

## Usage

    # Create a new project with the --buildpack option
    $ heroku create --buildpack https://github.com/omc/heroku-buildpack-kibana

    # ...Or update an existing project with heroku buildpacks:set
    $ heroku buildpacks:set https://github.com/omc/heroku-buildpack-kibana

    # Let the buildpack know where to find Kibana
    $ heroku config:set DOWNLOAD_URL="https://download.elastic.co/kibana/kibana/kibana-4.1.2-linux-x64.tar.gz"

    # Let Kibana know where to find Elasticsearch
    $ heroku config:set ELASTICSEARCH_URL="https://kibanauser:kibanapass@host.region.bonsai.io"

    # Create a Procfile to run the Kibana web server
    $ cat Procfile
    web: kibana --port $PORT

    # Push the above to trigger a deploy
    $ git push heroku master

    # Verify and profit!
    $ heroku open