# Informational Service Verification



{% tabs %}
{% tab title="Test Environment" %}
Once you have implemented the tracking code correctly, you will need the Chrome extension [Snowplow Chrome Extension](https://poplindata.com/open-source/snowplow-chrome-extension/) to verify if your base code is working correctly.

1. Install [Snowplow Chrome Extension](https://chrome.google.com/webstore/detail/snowplow-inspector/maplkdomeamdlngconidoefjpogkmljm)
2. On Chrome, navigate to the website with the base code installed.
3. Right-click on the page and click Inspect
4. Inside the Inspect console, click on the Snowplow Tab,

   ![image of snowplow tab in console](https://user-images.githubusercontent.com/43952553/66297087-80097d00-e8de-11e9-97b2-860745c78b19.png)

5. Refresh the page where the base code is installed, or navigate to a few tabs and see that Pageview event is populated.
6. Select on one of the Pageview event and you should see the image below

   ![Staging Snowplow Event](https://user-images.githubusercontent.com/43952553/66297499-500ea980-e8df-11e9-936e-94af863505cd.png)

   * Note:
     * APP name is `wogaa<websitename>staging`
     * Collector address is `snowplow.dcube.cloud`
{% endtab %}

{% tab title="Production Environment" %}
Once you have implemented the tracking code correctly, you will need the Chrome extension [Snowplow Chrome Extension](https://poplindata.com/open-source/snowplow-chrome-extension/) to verify the base code is working correctly.

1. Install [Snowplow Chrome Extension](https://chrome.google.com/webstore/detail/snowplow-inspector/maplkdomeamdlngconidoefjpogkmljm)
2. On Chrome, navigate to the website with the base code installed.
3. Right-click on the page and click Inspect
4. Inside the Inspect console, click on the Snowplow Tab,

   ![image of snowplow tab in console](https://user-images.githubusercontent.com/43952553/66297087-80097d00-e8de-11e9-97b2-860745c78b19.png)

5. Refresh the page where the base code is installed, or navigate to a few tabs and see that Pageview event is populated.
6. Select on one of the Pageview event and you should see the image below

   ![Production snowplow event](https://user-images.githubusercontent.com/43952553/66297226-cf4fad80-e8de-11e9-991d-10ec437b171d.png)

   * Note:
     * APP name is `wogaa<websitename>prod`
     * Collector address is `snowplow-web.wogaa.sg`

### Step 3. Login to WOGAA and check your site's status

When you have added the WOGAA Tracking code to your site, it will usually take less than 24 hours for your site to be verified. The verification of your site will be done automatically, however to be considered as verified, our WOGAA backed server must be able to detect or capture any events sending over from your site - you can visit the page yourself to speed the process up.

**Site - Pending Implementation and Verification** [  ](../images/web-analytics-is/IS_pending_verification.png)

Once WOGAA has detected any data/event that is sent from your site, the status of your registered site will be updated from "Pending Implementation and Verification" to the "Verified" state like the one shown below:

**Site - Verified** [  ](../images/web-analytics-is/IS_is_verified.png)

As soon as it is verified, an email notification will be sent to the Officer-In-Charge \(OIC\) of the Informational Service as a confirmation.
{% endtab %}
{% endtabs %}

