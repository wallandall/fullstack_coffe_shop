# Full Stack Coffee Shop
## Introduction

This application is a Full Stack Coffee Menu Application with an Ionic Frontend and a Flask API on the Backend

The  Full Stack Coffee Shop application performs the below actions:

1. Display graphics representing the ratios of ingredients in each drink.
2. Allow public users to view drink names and graphics.
3. Allow the shop baristas to see the recipe information.
4. Allow the shop managers to create new drinks and edit existing drinks.



## Backend Setup

The `./backend` directory contains the Flask API

### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

### Virtual Environment

From your project directory initialize and activate a virtualenv using the below commands:

```bash
 python -m virtualenv venv 
```


```bash
 source env/bin/activate 
```

>**Note** - In Windows, the `venv` does not have a `bin` directory. Therefore, you'd use the analogous command shown below:
    ```cmd
    env/Scripts/activate 
    ```

3. Install the dependencies from the backen directory:
   
    ``` pip install -r requirements.txt ```

4. Run the development server from the backend folder:
   
   ``` export FLASK_APP=flaskr ``` 

   ``` export FLASK_ENV=development ```

   ``` flask run --reload```
   
   >**Note** - for Windows CMD:

    ``` set FLASK_APP=flaskr ``` 

   ``` set FLASK_ENV=development ```
   
   ``` flask run --reload```

    >**Note** - for Windows PowerShell:

    ``` $env:FLASK_APP = "flaskr" ```  

   ``` $env:FLASK_ENV = "development" ```
   
   ``` flask run --reload ```


#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```



## Frontend Setup
The `./frontend` directory contains an Ionic frontend that consumes the data from the Flask server.

### Installing project dependencies

This project uses NPM to manage software dependencies. NPM Relies on the package.json file located in the `frontend` directory of this repository. After cloning, open your terminal and run:

```bash
npm install
```

### Configure Environment Variables

Ionic uses a configuration file to manage environment variables. These variables ship with the transpiled software and should not include secrets.

- Open `./src/environments/environments.ts` and ensure each variable reflects the system you stood up for the backend.

## Running Your Frontend in Dev Mode

Ionic ships with a useful development server which detects changes and transpiles as you work. The application is then accessible through the browser on a localhost port. To run the development server, cd into the `frontend` directory and run:

```bash
ionic serve
```

> _tip_: Do not use **ionic serve** in production. Instead, build Ionic into a build artifact for your desired platforms.
> [Checkout the Ionic docs to learn more](https://ionicframework.com/docs/cli/commands/build)


### Authentication

The authentication system used for this project is Auth0. `./src/app/services/auth.service.ts` contains the logic to direct a user to the Auth0 login page, managing the JWT token upon successful callback, and handle setting and retrieving the token from the local store. This token is then consumed by our DrinkService (`./src/app/services/drinks.service.ts`) and passed as an Authorization header when making requests to our backend.

### Authorization

The Auth0 JWT includes claims for permissions based on the user's role within the Auth0 system. This project makes use of these claims using the `auth.can(permission)` method which checks if particular permissions exist within the JWT permissions claim of the currently logged in user. This method is defined in  `./src/app/services/auth.service.ts` and is then used to enable and disable buttons in `./src/app/pages/drink-menu/drink-form/drink-form.html`.

############################### 

## Tasks

There are `@TODO` comments throughout the project. We recommend tackling the sections in order. Start by reading the READMEs in:

1. [`./backend/`](./backend/README.md)
2. [`./frontend/`](./frontend/README.md)

## About the Stack

We started the full stack application for you. It is designed with some key functional areas:

### Backend

The `./backend` directory contains a partially completed Flask server with a pre-written SQLAlchemy module to simplify your data needs. You will need to complete the required endpoints, configure, and integrate Auth0 for authentication.

[View the README.md within ./backend for more details.](./backend/README.md)

### Frontend

The `./frontend` directory contains a complete Ionic frontend to consume the data from the Flask server. You will only need to update the environment variables found within (./frontend/src/environment/environment.ts) to reflect the Auth0 configuration details set up for the backend app.

[View the README.md within ./frontend for more details.](./frontend/README.md)
