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

