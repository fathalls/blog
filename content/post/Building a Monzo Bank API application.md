+++
title = "Building a Monzo Bank API application"
icon = "credit-cards"
tags = [
    "openbanking",
]
date = "2019-08-14"
menu = "main"
summary = "How to build an app using the Monzo API."
+++


## Problem

I have three bank accounts across several banking providers. Everytime I need to find the total balance, I have to login to three different apps, check my balance in each of them and sum them up.

I needed an app which automates this work for me.

I started researching ways of doing this. I came across the [Open Banking initiative](https://www.openbanking.org.uk/customers/what-is-open-banking/). It allows individuals and businesses to access financial information with the approval of their customers. There exists a number of apps which offer this functionality. Most of them are paid.

## Solution

I decided to build a bank balance aggregator myself, using the Open Banking APIs across my bank providers. I took a look at the developers documentation for the three banks where I have accounts, Monzo is one of them. They have a very clear documentation, with step-by-step instructions on how to implement the OAuth2.0 flow.

I implemented a web app, using React for a basic front-end, Express in the back-end, managed by webpack.

### Set-up

We need to do a number of things before implementing OAuth:

**Credentials to access the API:**

1. Go to [Monzo's developers portal](https://developers.monzo.com/). You can sign-in using the email address linked to your Monzo account.
2. Add an OAuth client in the Client tab, this will create a profile for your app, where you define your redirect URI.
3. Keep client_secret and client_id generated in step 2, we will need these to get  access_token from the Monzo OAuth2.0 server.

**Setup the foundation for the application:**

Implement a minimal app which supports React, Babel, Node.js, Express, and is managed by webpack. The source code for a minimal configuration can be found [here](https://github.com/fathalls/react-express-webpack-boilerplate).

### Implementation

We need two configuration files to store the information about the client:

- <code>oauth_credentials</code>: a file for client parameters: client_id, client_secret and redirect_uri.
- oauth_urls: a file for the oauth endpoints - this is useful for code clarity.

To get the balance for an account, we need to follow these steps:

1. Get an authorisation code from Monzo's OAuth server - this will redirect the client to Monzo's portal.

        app.get("/monzopage", (req, res) => {
          res.redirect(
            urls.base_url +
              "?client_id=" +
              params.client_id +
              "&redirect_uri=" +
              params.redirect_uri +
              "&response_type=" +
              params.response_type +
              "&state=" +
              params.state
          );
        });

2. Exchange the authorisation code for an access token, store the latter and redirect to the home page (at this step I store the token in a global variable, this can be improved).

        app.get("/oauth/callback", (req, res) => {
          global.code = req.query.code;
          var client_id = params.client_id;
          var client_secret = params.client_secret;
          var redirect_uri = params.redirect_uri;
          var grant_type = params.grant_type;
          var url = urls.token_url;
        
          request.post(
            {
              url: url,
              form: {
                grant_type,
                client_id,
                client_secret,
                redirect_uri,
                code
              }
            },
            (err, response, body) => {
              var jsonBody = JSON.parse(body);
              global.access_token = jsonBody.access_token;
            }
          );
        
          res.redirect("/");
        });

3. Get the balance using the access token.We start by getting the account ID:

        app.get("/account", function(req, res) {
          var account_type = params.account_type;
          var access_token = global.access_token;
          var account_url = urls.account_url;
          request.get(
            {
              url: account_url + "?account_type=" + account_type,
              headers: {
                Authorization: "Bearer " + access_token
              }
            },
            (error, response, body) => {
              var jsonBody = JSON.parse(body);
              var account_id = jsonBody.accounts[0].id;
              res.json({
                account_id: account_id
              });
            }
          );
        });

    Then we get the balance for the given account ID:

        app.get("/balance", (req, res) => {
          var account_id = req.query.account_id;
          var balance_url = urls.balance_url;
          request.get(
            {
              url: balance_url + "?account_id=" + account_id,
              headers: {
                Authorization: "Bearer " + global.access_token
              }
            },
            (error, response, body) => {
              var balances = JSON.parse(body);
        
              res.json({
                balances: balances
              });
            }
          );
        });

The minimal React app makes these calls:

    import React from "react";
    import fetch from "isomorphic-fetch";
    
    class App extends React.Component {
      state = {
        account_id: "",
        balance: ""
      };
    
      loginToMonzo() {
        window.location.replace("/monzopage");
      }
    
      getBalance() {
        fetch("/account")
          .then(result => result.json())
          .then(response => {
            this.setState({ account_id: response.account_id });
            fetch("/balance?account_id=" + this.state.account_id)
              .then(result => result.json())
              .then(response => {
                this.setState({ balance: response.balances.balance });
              });
          });
      }
    
      render() {
        return (
          <div>
            <button onClick={e => this.loginToMonzo(e)}>Login to Monzo</button>
            <button onClick={e => this.getBalance(e)}>Get balance</button>
            <p>{this.state.balance}</p>
          </div>
        );
      }
    }
    
    export default App;

## Next steps

Hope this helped you understand how to interact with Monzo's API to obtain the balance. We can improve it by:

- Implementing the access token refresh mechanism.
- changing the access token storage to be more secure - in a database for instance.
- Implementing a minimalist design for the page - currently sketching :).

If you get stuck with any step or need help, you can reach out to me via [Twitter](https://twitter.com/fathalls_).
