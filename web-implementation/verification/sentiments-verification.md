# Sentiments Verification

You will need the Chrome extension [Snowplow Chrome Extension](https://poplindata.com/open-source/snowplow-chrome-extension/) to verify the base code. The following steps work for both staging and production setup.

1. Install [Snowplow Chrome Extension](https://chrome.google.com/webstore/detail/snowplow-inspector/maplkdomeamdlngconidoefjpogkmljm)
2. Verify that Sentiments is loaded correctly.
3. Right-click on the page and click Inspect
4. Inside the Inspect console, click on the Snowplow Tab,

   ![image of snowplow tab in console](https://user-images.githubusercontent.com/43952553/66297087-80097d00-e8de-11e9-97b2-860745c78b19.png)

5. Refresh the page and see that Pageview event is populated. [  ](../images/snowplow/page-view-event-ss.png)
6. Submit a rating and you will see the sentiment rating event as shown below. [  ](../images/snowplow/sentiment-rating-event-ss.png)
7. Submit questions to populate sentiment feedback events as shown below. [  ](../images/snowplow/sentiment-question-event-ss.png)

