# Chatbot-development-user-study
## Introduction 
In the following, we explain the required steps in order to configure DF-Chatbot and then interact with it. All these steps are demonstrated in this [video](https://drive.google.com/file/d/1p7CdlVTkFAB-SRiqrmysSz4ac8hRZt7_/view?usp=sharing).

## How to configure Dialogflow CX Agent? 
1. Download the source code in this github project. The source code includes the following files:
 - Study_Agent.blob: contains necessary intents, training phrases, and entities for this user study.
 - webhook_service:
2. Go to [DialogFlow CX console](https://dialogflow.cloud.google.com/cx/projects) and connect to the console with your gmail
3.  Create a new google cloud project and enable DialogFlow API.
4.   Create a new empty agent.
5.   Go to "View all agents" in the current project and restore Study_Agent.

## How to run and deploy the webhook service? 
1. To execute some actions, the agent will need to invoke specific APIs, namely [here](https://developer.here.com/); [openweathermap](https://openweathermap.org/api); [Yelp](https://www.yelp.com/developers/documentation/v3). To use these APIs you need to get credential information mentioned in API_credentials.json file in the webhook_service folder and complete them. Getting credential information requires creating accounts in these APIs.
2. Once you get the required credentials and complete API_credentials.json file, open terminal, create a virtual environment and install required packages.
 - Operating system: macOS/OS X, Linux; 
```
pip install virtualenv
cd webhook_service
virtualenv -p python3 myenv
source myenv/bin/activate
pip install -r requirements.txt
python webhook.py
```

- Operating system: Windows:

```
cd webhook_service
python3 -m venv myenv
myenv\Scripts\activate.bat
pip install -r requirements.txt
python webhook

3.  Open new terminal to run ngrok server: if you don't have ngrok configured in your laptop, just Download it from [here](https://ngrok.com/download), unzip it, and in the terminal just run the following commends:

```
cd Path_To_Ngrok
./ngrok http 8081 (or ngrok http 8081 if the first one does not work)

```

4.Setup webhook in Dialogflow:
 - Create first a webhook:
    - Select the Manage tab.
    - Click Webhooks, Click Create and put "my_webhook_service" as display name .
    - Enter your webhook url generated by ngrok, some thing like https://2f4168d1c17d.ngrok.io/my_webhook.
    - Click Save.
 - Once the webhook is created, you will need to add it to each fulfilment that requires calling this webhook. Please note you have to precise the fulfilment tag that indicates which action needs to be executed.






