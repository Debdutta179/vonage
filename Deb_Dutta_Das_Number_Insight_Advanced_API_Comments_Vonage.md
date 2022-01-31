
# Number Insight Advanced API

My comments are as follows:
* Add the title **Overview** before writing the introduction; it enhances search engine optimization. So, search engines can easily retrieve the information when a user is enquiring for this data.

    Rewrite to:  

  # Number Insight Advanced API
    ## Overview

* Rewrite the introductory sentence as follows:

    "You can use the Number Insight Advanced API to assess the risk associated with a number. This API provides the following information, in addition to the data returned in the [Number Insight Standard API](https://developer.vonage.com/number-insight/code-snippets/number-insight-standard):"

* A few grammatical errors:  
   * Replace all 'If' in the overview section with 'whether' because 'If' denotes a condition; for example, if it rains, I will not go to school.  
      "If the number is likely to be valid"  

      Rewrite to:  
      "whether the number is valid"

   * "If the number is reachable (not available in US)"  

      Rewrite to:  
      "whether the number is accessible (this function is unavailable in the United States of America)    
      US is not the correct abbreviation of the United States of America. It is U.S. and, it is always recommended to use full forms, instead of the abbreviated form of a word.  

 * "If the number is roaming and, if so, the carrier and country"   

     Rewrite to:  
     "whether the number is roaming and, if yes, the carrier and the country."  
     The carrier and country implies that the carrier and country are  same. They are not identical; hence, use 'the' to denote two separate nouns.

 *  Insert 'other' in the note table and rewrite the information as follows:  
    "Note that the Number Insight Advanced API does not provide any **additional** information about landlines, other than the data retuned by the Number Insight Standard API. For more information on landline numbers, use the Standard API."  

* Organize the remaining sections in the following manner because it helps a user to easily search for the information they are looking for (if possible, make each bullet pointer a collapsible section):  
 * Method
 * Endpoint

  * Parameter  

 |Parameter | Value | Description
 |-----| -----------| -----------
 |api_key|$VONAGE_API_KEY | The API key that is available on the Vonage dashboard.


 * Sample URL

 * API Request Sample

<ul>After this bullet pointer, include tabs as per each technology (curl (Linux), Node.js, java, .NET, PHP, Python, and Ruby).</ul>


 * Sample Response
 * Webhook Workflow
