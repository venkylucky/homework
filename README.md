<table>
  <tr><td>
  homework!
  </td>
    <td>
        <a href=#Placeholder>Placeholder</a> |
        <a href=#Placeholder>Placeholder</a> |
        <a href=#Placeholder>Placeholder</a>
    </td>
  </tr>
  <tr>
    <td width=15%>
    <img src=img/icon.png style="width:150px"></td>
    <td>605 is a media measurement and analytics firm that harnesses viewership data to provide research & insights for brands, entertainment marketers, and programmers.  <br/><br/>
    This repo houses homework exercises for new candidates
    </td>
  </tr>
</table>

## Before You Start

Before you get started, you should have already received requests for following information via email:

1.  Your github.com username.  Candidate homework submissions should be forked from this repo, then a pull request should be submitted. We use pull requests every day to collaborate at work, and wish to conduct interviews along the same lines.  Depending on time available for our engineers, there might even be a little bit of back-and-forth traffic along the lines of questions or change requests.

2. Your keybase.io username.  Please create an account if you don't already have one.  We will probably ask you to actually deploy things, and for this we'll need a way to encrypt secrets for your eyes only.

3. Your best guess as to your time commitment.  We don't like partial or incomplete homework submissions, but we also understand that life happens and people are busy.  We will take your time commitment under consideration when we're evaluating your work.

*Make sure your contact at 605 already has this information before you submit a PR.*

## Homework Goals

The purpose of this exercise is to create the automation to set up as much of a production ready setup as possible for a simple web app.  

This exercise, like most things in real life, is at least a little bit time-sensitive.  You will need to make decisions about what to concentrate on, and what to let slide.  Please document the choices you make.

## Deliverables

1. All automation to set up the infrastructure
1. Instructions on how to run it
1. README documenting your choices, including choices you had to make due to time pressure, deviations from best practice or production set up, a description of the set up, and anything else you think would be good to know.
1. The time spent

The entire solution should be under source control with reasonable commit messages and structure so that we can get a sense of the time spent.  In other words, don't give us a tarball, don't commit everything in one big push, don't use 2 letter commit messages, etc.

## The Actual Exercise

Please deploy the Airflow web app (i.e. no need for the scheduler or flower components) together with its necessary dependencies, of a postgres database and redis server.  

* Versions used, and manner of deployment are up to you.  
* Airflow is a python based app. You can find it on github [here](https://github.com/apache/incubator-airflow).
* Imagine that there's a risk that we'll have a lot of traffic on this site.

Airflow itself is not the point here - it's an example of an app that needs a database and some other supporting infrastructure. Feel free to document any oddities you find that you believe need airflow configuration that you choose not to tackle.

Don't worry about all the configuration, or even understanding what airflow does. The following configuration will be most relevant to you. You may or may not need this, and the values may or may not be correct for your setup - feel free to modify them.


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
