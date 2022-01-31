

#  Number Insight Advanced API

## Overview  
You can use the Number Insight Advanced API to assess the risk associated with a number. This API provides the following information, in addition to the data returned in the [Number Insight Standard API](https://developer.vonage.com/number-insight/code-snippets/number-insight-standard):  
* whether the number is valid
* whether the number is accessible (this function is unavailable in the United States of America)  
* whether the number is roaming and, if yes, the carrier and the country  


|  Note |Description   |
|---|---|
|:information_source:| The Number Insight Advanced API does not provide information about landlines, other than the information returned by the [Number Insight Standard API](https://developer.vonage.com/number-insight/code-snippets/number-insight-standard). For more information on landline numbers, use the [Number Insight Standard API](https://developer.vonage.com/number-insight/code-snippets/number-insight-standard).   

## Method

<font color="red"> `GET` </font>  

## Endpoint

```
https://vonage_server:port/ni/advanced/async/json
```

## Parameters

 The following table explains the parameters that you can send in a request to the Number Insight Advanced API:  

|Parameter | Value | Description
|-----| -----------| -----------
|api_key|$VONAGE_API_KEY | The API key that is available on the Vonage [dashboard](https://identity.nexmo.com/login).
|api_secret|$VONAGE_API_KEY | The API secret that is available on the Vonage  [dashboard](https://identity.nexmo.com/login).  
|number| $INSIGHT_NUMBER | The specific number for which you want to retrieve detailed information from the API.  

--------------------------------------------------------------------------------  

**Note**: Replace the parameter placeholder values with real data when you send the request.  

--------------------------------------------------------------------------------

## Sample URL

 ```
 https://api.nexmo.com/ni/advanced/async/json?api_key=$VONAGE_API_KEY&api_secret=$VONAGE_API_SECRET&number=$INSIGHT_NUMBER&callback=$WEBHOOK_URL
 ```

--------------------------------------------------------------------------------  

**Note**: Vonage recommends to make an asynchronous request to the Number Insight Advanced API because synchronous calls might get timed out.  

-------------------------------------------------------------------------------


## API Request Sample  

<details>

<summary> <b>Curl</b> </summary>

**Request Implementation**  
Add the following to `ni-advanced-async.sh`:

```
curl "https://api.nexmo.com/ni/advanced/async/json?api_key=$VONAGE_API_KEY&api_secret=$VONAGE_API_SECRET&number=$INSIGHT_NUMBER&callback=$WEBHOOK_URL"
```

**Request Execution**  
Save the file to your machine and run it:

```
sh ni-advanced-async.sh
```

</details>

<details>

<summary> <b>Node.js</b> </summary>


**Prerequisites**
* Dependencies installation:  

```
npm install @vonage/server-sdk
```
* Dependencies initialization:  
1. Create a file `ni-advanced-async-client.js` and add the following code:  

```
const Vonage = require('@vonage/server-sdk');

const vonage = new Vonage({
  apiKey: VONAGE_API_KEY,
  apiSecret: VONAGE_API_SECRET
});
```
2. Save the file to your machine and run it:  

```
sh ni-advanced-async.sh
```

**Request Implementation**  

Add the following to the `ni-advanced-async-client.js`:

```
vonage.numberInsight.get({
  level: 'advancedAsync',
  number: INSIGHT_NUMBER,
  callback: 'https://demo.ngrok.io/webhooks/insight'
}, (error, result) => {
  if (error) {
    console.error(error);
  }
  else {
    console.log(result);
  }
});  
```

**Request Execution**  

Save the file to your machine and run it:

```
node ni-advanced-async-client.js
```
</details>

</details>

<details>

<summary> <b>Java</b> </summary>


**Prerequisites**

* Dependencies installation:  
Add the following to `build.gradle`:

```
compile 'com.vonage:client:6.2.0'
```
* Dependencies initialization:  
Create a class named <font color="red"> `AdvancedInsightAsync`</font> and add the following code to the <font color="red"> `main` </font> method:

```
VonageClient client = VonageClient.builder()
        .apiKey(VONAGE_API_KEY)
        .apiSecret(VONAGE_API_SECRET)
        .build();
```

**Request Implementation**  
Add the following to the <font color="red"> `main` </font> method of the <font color="red"> `AdvancedInsightAsync`</font> class:

```
InsightClient insightClient = client.getInsightClient();

AdvancedInsightRequest request = AdvancedInsightRequest.builder(INSIGHT_NUMBER)
        .async(true)
        .callback(CALLBACK_URL)
        .build();
insightClient.getAdvancedNumberInsight(request);
```

**Request Execution**  
1. Update your <font color="red"> `build.gradle` </font> with the following:

```
apply plugin: 'application'
  mainClassName = project.hasProperty('main') ? project.getProperty('main') : ''
```
2. Run the following <font color="red"> `gradle` </font> command to execute your application (replace <font color="red"> `com.vonage.quickstart.insight` </font> with the package containing <font color="red"> `AdvancedInsightAsync` </font>):

```
gradle run -Pmain=com.vonage.quickstart.insight.AdvancedInsightAsync
```

</details>

## Sample Response

```
{
    "request_id": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
    "number": "447700900000",
    "remaining_balance": "10.000000",
    "request_price": "0.03000000",
    "status": 0
}
```

## Webhook Workflow  

After the response message is received, it is sent to the specified webhook via a <font color="red"> `POST` </font> request. See the [Number Insight Advanced Webhook](https://developer.vonage.com/number-insight/code-snippets/number-insight-advanced-async-callback/node) code snippet to learn more about coding the webhook handler.
