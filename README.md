<table>
  <tr><td>
  homework!
  </td>
    <td>
        <a href=#overview>Overview</a> |
        <a href=#prerequisites>Prerequisites</a> |
        <a href=#workflows>Workflows</a>
    </td>
  </tr>
  <tr>
    <td width=15%>
    <img src=img/icon.png style="width:150px"></td>
    <td>

    Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.
    </td>
  </tr>
</table>

## Devops Exercise

Before you start, you should have already nominated how long you plan to spend on this, so we know what kind of time pressure you are working against. If you haven't done that yet, please read through these instructions and email us your nominated amount of time.


## Goal
The purpose of this exercise is to create the automation to set up as much of a production ready setup as possible for a simple web app.

Because this exercise is timed, you will need to make decisions about what to concentrate on, and what to let slide. Please document the choices you make.


## Deliverables
All automation to set up the infrastructure
Instructions on how to run it
README documenting your choices, choices you had to make due to time pressure, deviations from best practice or production set up, a description of the set up, and anything else you think would be good to know.
The time spent
Preferred if the whole package could be under source control so that we can get a sense of the time spent.


## The Actual Exercise

Please deploy the Airflow web app (i.e. no need for the scheduler or flower components) together with its necessary dependencies, of a postgres database and redis server.

Versions used, and manner of deployment are up to you.

Airflow is a python based app. You can find it on github here: https://github.com/apache/incubator-airflow

Imagine that there's a risk that we'll have a lot of traffic on this site.

Airflow itself is not the point here - it's an example of an app that needs a database and some other supporting infrastructure. Feel free to document any oddities you find that you believe need airflow configuration that you choose not to tackle.

Don't worry about all the configuration, or even understanding what airflow does. The following configuration will be most relevant to you. The values may or may not be correct for your setup - feel free to modify them.


```
# The SqlAlchemy connection string to the metadata database.
# SqlAlchemy supports many different database engine, more information

# their website

sql_alchemy_conn = postgresql+psycopg2://<rest of url>

# Whether to load the examples that ship with Airflow. It's good to

# get started, but you probably want to set this to False in a production

# environment

# Gives us something to look at to set this to true.

load_examples = True

[webserver]

# The base url of your website as airflow cannot guess what domain or

# cname you are using. This is used in automated emails that

# airflow sends to point links to the right web server

base_url = http://localhost:8080

# The ip specified when starting the web server

web_server_host = 0.0.0.0

# The port on which to run the web server

web_server_port = 8080

# The Celery broker URL. Celery supports RabbitMQ, Redis and experimentally

# a sqlalchemy database. Refer to the Celery documentation for more

# information.

broker_url = redis://redis:6379/1

# Another key Celery setting

celery_result_backend = db+postgresql://<rest of url here>

```

We look forward to hearing back from you soon. And of course any questions and comments are welcome!
