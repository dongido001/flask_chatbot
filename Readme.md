# How to build a chat bot with Flask, Pusher Channels and Diaglogflow

This is a demo application showing how to build a Chat bot using Flask, Dialogflow and Pusher. You can read the tutorial on how it was built [here](https://pusher.com/tutorial/)

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

This tutorial uses the following:

 - Python 3.6 (You should have python 3.6 or higher version installed)
 - Pusher Channels (Create an account [here](https://dashboard.pusher.com/accounts/sign_up) or [login](https://dashboard.pusher.com/accounts/sign_in) here)
 - JavaScript (jQuery)
 - Dialogflow (Create an account [here](https://dashboard.pusher.com/accounts/sign_up) or [login](https://dashboard.pusher.com/accounts/sign_in) here)
 - [Ngrok](https://ngrok.com/download) (Download it here if you don't have it downloaded already)

### Setting up the project

First of all, clone the repository to your local machine:

```sh
 $ git clone https://github.com/dongido001/flask_chatbot.git
```

Next, create your environment keys:

```
cp .env.example .env
```
There are couple of keys you need to set in the '.env' file. The next section will show you how you can get this keys.

#### Pusher

Login to Pusher [account](https://dashboard.pusher.com/accounts/sign_in), create a new app and then get your API keys.

 Next update the following keys in the `.env` file with the correct keys:
  ```
  PUSHER_APP_ID=app_id
  PUSHER_KEY=key
  PUSHER_SECRET=secret
  PUSHER_CLUSTER=cluster
  ```

#### Dialogflow

You also need to create a Dialogflow account. Create it [here](https://console.dialogflow.com/api-client/#/login) or [login](https://console.dialogflow.com/api-client/#/login) if you have an account already.

Next,
  - Create a new agent called named `Movie-bot`
  - Create an Intent named `movie`
  - Create an Entity named `movie`
  - Then enble the intent to use webhook
  - Finally, on your Dialogflow console page, click on Fulfillment then enable webhook. 

Now, get your Dialogflow API key. Head to Google cloud [here](https://console.cloud.google.com/apis/credentials/serviceaccountkey)

Then,
  - Select `Dialogflow integrations` under `Service account`. 
  - Then select `JSON` under `key type`. 
  - Next, make sure at the top menu that our bot is selected as the project name - `Movie-Bot`
  - Finally, click on the Create button to download the your API key

  Your API key will be downloaded automatically. It's a JSON file. We'll need the file soon.

 Next, copy the downloaded file to the root folder of the project - `flask_chatbot`

 Then, update the keys in the .env file with the correct information:
 ```
 GOOGLE_APPLICATION_CREDENTIALS=*.json
 DIALOGFLOW_PROJECT_ID=project_id
 ```
 **Note**
   - `*.json` is the name of the JSON file you just copied to the root folder of the project.
   - To get your `project_id`, open the JSON file with your code editor, you will see a field - "project_id". The value is your `project_id`


#### OMDb API key

We are using [OMDb](http://www.omdbapi.com/) to fetch details of a movie. So you need to get an API key.

To get a free API access key, head to [OMDb](http://www.omdbapi.com/apikey.aspx). Enter the required details, then submit the form. An email will be sent to you that contains your API key. You also need to activate your account from the email sent to you.

Once you have your key, update the information in the `.env` file with the correct detail:

```
OMDB_API_KEY=API_KEY
```

### Running the App

To get the app running:

 - From a command line, cd into the project root folder - `flask_chatbot`
 - Creat a virtual environment:
 ```
 python3 -m venv env
 ```
 - Activate the virtual environment:
 ```
   source env/bin/activate
 ```
 On windows? Activate it with the below:
 ```
   Scripts\activate
 ```

 - Install the dependencies:
 ```
 pip install -r requirements.txt
 ```

 - Finally run the app:
 ```
  flask run
 ```

 Congrats! The app should now be running on http://localhost:5000

## Built With

* [Flask](http://flask.pocoo.org/) - A microframework for Python
* [Pusher](https://pusher.com/) - APIs to enable devs building realtime features
* [Dialogflow](https://dialogflow.com/) A Google-owned developer of human–computer interaction technologies based on natural language conversations
