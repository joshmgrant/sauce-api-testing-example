# Sauec Labs API Testing - An Example 

The structure of this repository contains

- A simple [Flask](https://flask.palletsprojects.com/en/1.1.x/) application for creating a "Sauce Log", a database for a list of hot sauces and their descriptions, and
- A fairly simple API test framework written using [pytest](https://pytest.org) and [requests](https://docs.python-requests.org/en/master/).

The workshop shall walk through the API app and test framework.

## Before You Start

This is a Python project, so you will need Python 3.7+ installed on your machine. An IDE such as PyCharm or VS Code is recommended.

## Installing And Setting up the Project

Please clone this repo since there are some tags that are used for the workshop. You can also download the ZIP file of this repo to work with the final product. 

### Virtual Environment

To install the product, first create a Python [virtual environment](https://realpython.com/python-virtual-environments-a-primer/) by running this in the directory you just cloned:

```
python3 -m venv venv
```

then activate the virtual environment. If you are using Mac/Linux, use the following command to active your Virtual Environment:

```
source venv/bin/activate 
```

If you are using Windows, use the following command to active your Virtual Environment:

```
.\venv\bin\Activate.psl
```

Your terminal should have `(venv)` at the start of it once the virtual environment is activated. You can also use PyCharm to handle virtual environments. 

### Installing Dependencies

To install dependencies, run

```
pip install -r requirements.txt
```

You should be ready to go! 

## Starting the Flask App

If you like skipping ahead, you can initialize the database and start the app by running the following commands (note the order, which is important):

```
python create_db.py
gunicorn --bind 0.0.0.0:5000 main:app &
```

This will start the app locally on port 5000. You can check that this is up and running by executing

```
curl http://localhost:5000/sauce_logs
```

in a terminal window or pasting

```
http://localhost:5000/sauce_logs
```

in a browser window such as Chrome or Firefox.

If you are unable to use `gunicorn` because you are on Windows or another platform not supported by it, you can also use the Flask development server by running:

```
FLASK_APP=main.py flask run
```

In either case, you should see a nice welcome message. 

## Running the API Tests

Once you have the app up and running, you can run the tests by executing

```
pytest
```

All tests should pass. If they do not, check that the app is running on port 5000.
