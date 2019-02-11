# HairForceOne
```bash
# Via putty (psftp):
lcd c:/...
put poc-2019.zip

# on your raspberrypi
unzip poc-2019.zip
cd poc-2019

# create the venv and activate it
sudo apt-get install python3-venv
python3 -m venv venv
. venv/bin/activate

# Install the requirements and the hfo module into the venv
pip install -e .
sudo apt-get update

The app can be configure using an config.cfg file in the instance directory.
mkdir instance
cd instance 
nano config.cfg
```python
APP_VERSION='0.1poc'
SECRET_KEY='my_secret'
```
cd ..

The database is create in the instance directory. The following command line options are available:
```bash
# create a new database
pip install flask
flask init-db

# Recreate the database and fill with some demo data
flask fill-db
```

# Run the hfo flask app, ALWAYS ALL THREE LINES
export FLASK_APP=hf1
export FLASK_ENV=development
flask run -h 0.0.0.0 -p 5555
```




When using VS Code, you can debug the app with the follwing ```launch.json```
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: Flask",
            "type": "python",
            "request": "launch",
            "module": "flask",
            "env": {
                "FLASK_APP": "hf1",
                "FLASK_ENV": "development"
            },
            "args": [
                "run",
                "--no-debugger",
                "--no-reload"
            ],
            "jinja": true
        }
    ]
}
```
