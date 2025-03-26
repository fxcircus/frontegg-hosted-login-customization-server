# Frontegg Hosted Login Box Customization Overrides Server

This project includes a Node.js server designed to manage metadata overrides for customizing the Frontegg login box.

In hosted mode, it is necessary to deploy a server or Lambda function. When the login box is loaded, Frontegg will send a GET request to your server to retrieve the appropriate localizations.


## Prerequisites

- Node.js and npm (or yarn) installed on your development machine.
- A Frontegg account with a project and environment set up.


## Setup

1. Use the Frontegg builder to achieve the desired visual style for your login box, such as color changes, font choices, and logo placements.


2. Clone this repo and choose a hosting platform like Heroku or a similar service that suits your needs. Deploy your code to the chosen platform. Once deployed, obtain the publicly accessible URL of your server. It should look like https://yourserveraddress/overrides.

3. Follow [the instructions here to implement Frontegg Metadata Overrides](https://docs.frontegg.com/docs/hosted-and-embedded-setup#getting-started-with-metadataoverrides) to connect your hosted login box to the server.

4. Load your hosted login box (The `Login URL` from `Frontegg Portal ➜ [ENVIRONMENT] ➜ Env Settings page`, followed by `/account/login`). For example - `https://app-frtqiefxjqn9.frontegg.com/oauth/account/login`. You should see the settings are applied.

5. If you do not see the settings applied, open the network tools, refresh the page, and search for a request from `/overrides` to see if your server was called. You can also search for the call from `/metadata?entityName=adminBox` to verify that your are passing `metadataOverrides` under `configuration` as required.

```

"metadataOverrides": {
    "url": "https://yourserveraddress/overrides"
}

```
