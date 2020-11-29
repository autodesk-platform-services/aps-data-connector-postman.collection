# Postman Collection for BIM360 Data Connector API 

[![Postman](https://img.shields.io/badge/Postman-v7-orange.svg)](https://www.getpostman.com/)

![Beginner](https://img.shields.io/badge/Level-Beginner-green.svg)
[![License](https://img.shields.io/:license-MIT-blue.svg)](http://opensource.org/licenses/MIT)

## Description

This repository provides demos for the category of [BIM360 Data Connector API](TBD) . Right now, the APIs can:
 - Create requests with the scheduleInterval: one time, by day, by week, by month or by year
 - Get requests collection, single request, jobs of request
 - Get single job, extracted data list, and signed url of extracted data
 - Patch or delete request
 
The API supports 3 legged token only.

## What's Postman?

Postman is a popular tool that provides an easy-to-use interface to send HTTP requests. Postman is able to parse the responses that Forge sends you and save response parameter values to variables. These parameters can then be reused in subsequent requests through these variables. The Postman collections in this repository use this ability to provide pre-populated HTTP requests to help you follow the tutorial workflow with minimal effort. You can also modify the requests and experiment without having to write a single line of code. 

- You can learn how to install and use Postman from [here](https://learning.getpostman.com/docs/postman/launching_postman/installation_and_updates).

- You can download the Postman installer from [here](https://www.getpostman.com/downloads/).


## Setup

1.  **Forge Account**: Learn how to create a Forge Account, activate the subscription and create an app by [this tutorial](http://learnforge.autodesk.io/#/account/). Get Forge _client id_, _client secret_ and  _callback url_. Please register Forge app with the _callback url_ as 

    ```https://www.getpostman.com/oauth2/callback```

2. **BIM 360 Account and project**: must be Account Admin to add the app integration. [Learn about provisioning](https://forge.autodesk.com/blog/bim-360-docs-provisioning-forge-apps). Make a note with the __account name__

3. Since the API requires 3 legged token, and as [product help](https://knowledge.autodesk.com/support/bim-360/learn-explore/caas/CloudHelp/cloudhelp/ENU/BIM360D-Insight/files/BIM360D-Insight-data-extractor-html-html.html) indicates, this user must have the **Executive Overview** access enabled.  

4. Get BIM360 account id (hub id without b.) by API , or copy from BIM360 UI. 

5.  Clone this repository or download it. It's recommended to install [GitHub Desktop](https://desktop.github.com/). To clone it via command line, use the following (**Terminal** on MacOSX/Linux, **Git Shell** on Windows):

    ```git clone https://github.com/xiaodongliang/forge-bim360-data.connector.api-postman.collection```

6. Import the collection and environment files to Postman

6. In environment, input _client id_, _client secret_, _hub id_ , and _callbackUrl_. _callbackUrl_ is your own callback endpoint that Data Connector API will notifiy you when the extracting job is done. For test purpose, [RequestBin](https://requestbin.com/) is a nice tool to produce custom webhook (callback). Data Connector will also send email nortification to the user who submits the request. So _callbackUrl_ is not a must.

   <p align="center"><img src="./help/apiref-env.png" width="800" ></p>  

7. In context menu of collection >> **Edit**, switch to the tab **Authorization**. Click **Get New Access Token**, input the variables as below:

   - Grant Type ``Authorization Code``
   
   - Callback URL  ``https://www.getpostman.com/oauth2/callback``

   - Auth URL  ``https://developer.api.autodesk.com/authentication/v1/authorize``

   - Access Token URL  ``https://developer.api.autodesk.com/authentication/v1/gettoken``

   - Client ID ``{{client_id}}``

   - Client Secret ``{{client_secret}}``

   - Scope ``data:read data:write data:create``

   - Client Authentication ``Send Client credentials body``

   <p align="center"><img src="./help/apiref-oauth2.png" width="800" ></p> 
 
 8. Click **Request Token**, it will direct to login Autodesk account, after it succeeds, the token will be generated. Click **Use Token**. Then, click **Update** to close the window of **Edit**

   <p align="center"><img src="./help/token.png" width="600" ></p> 
   
   RFI API requires to work with 3-legged token. This collection takes **[Inheriting auth](https://learning.getpostman.com/docs/postman/sending-api-requests/authorization/#inheriting-auth)** to apply 3-legged token to every endpoint in the collection automatically, which means it does not need to input the token in the header explicitly.

## API Test

1. Assume the steps of **Setup** have been performed. The access token is ready.

2. Play the scripts. Try to change some parameters or body with more scenarios. 
   <p align="center"><img src="./help/collection.png" width="600" ></p>   


## Notes
1.  
 

## License

This sample is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT). Please see the [LICENSE](LICENSE) file for full details.

## Written by

Xiaodong Liang [@coldwood](https://twitter.com/coldwood), [Forge Partner Development](http://forge.autodesk.com)
