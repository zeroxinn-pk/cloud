https://cloud.google.com/free


#Application(app.py) code:

import os


from flask import Flask

app=Flask(__name__)

@app.route('/')

def helo_youtue():

    target = os.environ.get('Target',  'HELLO YOUTUBE!!') 
    
    return 'HELLO {}!\n'.format(target)

if __name__ == "__main__":   

app.run(debug=True,host='0,0,0,0',port=int(os.environ.get('PORT',8080))))


#Docker file code:

# USE light weight Python 3.7 image.

# https://hub.docker.com/_/python

FROM python:3.7-slim

# Copy local code to thecontainer image.

ENV APP_HOME /app
WORKDIR $APP_HOME
COPY . ./

# Install production dependencies.

Run pip install Flask gunicorn

# Run the web service on container setup. Here we use the gunicorn

# webserver, with one worker process and 8 threads.

CMD exec gunicorn --bind :$PORT --workers 1 --threads 8 --timeout 0 app:app

