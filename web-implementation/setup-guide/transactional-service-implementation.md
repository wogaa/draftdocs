---
description: >-
  This document is a guide to implement and verify WOGAA event trigger codes on
  your site.
---

# Transactional Service Implementation

## Prerequisite

For implementation of code in Test and Production environment,

Please ensure that you have done the following before you proceed

1. Successfully implemented wogaa.js v2 code for Informational Service  \( [Implementation and Verify Guide for Informational Service](/web-analytics/web-implement-and-verify/) \)
2. Collate Transactional Service's tracking ID \( [How to get your tracking ID]() \)
3. Also, [see the information](/web-analytics/web-types-of-ts-scenarios) on where to place the event trigger codes based on the types of Transactional Service design structure.

!!! info For code implementation of multiple transactional services, we recommend you to collate all the unique tracking ID for each service required.

## Implement and Verify Event Code

Please ensure you have the tracking ID for the services you wish to implement event tracking code for. \( [How to get your tracking ID]() \)

There are 2 event trigger codes for you to use

1. Event trigger code to start tracking the transactional services

   ```javascript
   window.wogaaCustom.startTransactionalService('<tracking_id>')
   ```

2. Event trigger code to end tracking the transactional services

   ```javascript
   window.wogaaCustom.completeTransactionalService('<tracking_id>')
   ```

!!! tip The correct tracking ID should be passed to `startTransactionalService` and `completeTransactionalService`.

```text
If the tracking ID passed to either of the event trigger code doesn't belong to your website, event trigger code will not work.
```

!!! example Transactional service belonging to Example Website \(`www.example.gov.sg`\)

| Name of Transactional service | Tracking ID |
| :--- | :--- |
| Creation of user | `example-1` |
| Apply for approval | `example-2` |

??? question "When should I invoke `startTransactionalService` and `completeTransactionalService`?" `window.wogaaCustom.startTransactionalService('example-1')` should be invoked when the website user starts the transactional service `Creation of user`

```text
`window.wogaaCustom.completeTransactionalService('example-1')` should be invoked when the website user completes the transactional service `Creation of user`
```

??? question "What argument should I pass to `startTransactionalService` and `completeTransactionalService`?"

* Invoking `window.wogaaCustom.startTransactionalService('example-1')` will work since the Example Webite `www.example.gov.sg` has tracking ID `example-1` tagged under it.
* Invoking `window.wogaaCustom.startTransactionalService('testing-1')` will not work since the Example Webite `www.example.gov.sg` doesn't have tracking ID `testing-1` tagged under it.

### Verification

#### Verify if your site is sending both events

We will need the Chrome extension [Snowplow Chrome Extension](https://poplindata.com/open-source/snowplow-chrome-extension/) to verify the base code

1. Install [Snowplow Chrome Extension](https://chrome.google.com/webstore/detail/snowplow-inspector/maplkdomeamdlngconidoefjpogkmljm)
2. On Chrome, navigate to the website with the base code installed.
3. Right-click on the page and click Inspect
4. Inside the Inspect console, click on the Snowplow Tab,

   ![image of snowplow tab in console](https://user-images.githubusercontent.com/43952553/66297087-80097d00-e8de-11e9-97b2-860745c78b19.png)

5. Refresh the page where the base code is installed and see that `Structured Event: transactionalService` event is populated.
6. Select on one of the `Structured Event: transactionalService` events as shown below:

   ![Staging Snowplow Event](https://user-images.githubusercontent.com/387000/83584083-aa4c3100-a578-11ea-9390-8d7171ac6407.png)

   ![Staging Snowplow Event](https://user-images.githubusercontent.com/387000/83584089-afa97b80-a578-11ea-95e4-f4bd8aac827d.png)

   * Note:
     * Event action is either `start` or `complete`
     * Collector address for staging is `snowplow.dcube.cloud`
     * Collector address for production is `snowplow-web.wogaa.sg`
     * `start` event and `complete` event could be in different locations on your site. In this case, you may only see one event at a time. Navigate to the page where you installed code, and verify both events are triggered in their respective page.

#### Verify if Wogaa server is receiving both events

The verification of Transactional Service on the server side is done automatically, however to be considered as verified, both `startTransactionalService` and `completeTransactionalService` events must be captured by our backend server.

It may take up to 24 hours for the verification. Once verified, we send out an email notification to Officer In Charge \(OIC\) for the Transactional Service. Please let us know if there is any issues with regards to this via wogaa@tech.gov.sg

#### Self service verification tool \(staging only\)

This tool allows you to verify if your implementation is working correctly in your test or staging environment by showing the past 7 days' transaction count. Please note it will not query the events from production server.

Please check if your test or staging setup is using the following script

```markup
<script src="https://assets.dcube.cloud/scripts/wogaa.js"></script>
```

Then use this tool to check your transactional service events by either providing the `domain` of your test server or staging server, or providing the `tracking_id` of your transactional service. Please omit `http://` or `https://` when providing the `domain`

## How to Get Your Tracking ID

1. Login to wogaa.sg
2. View your respective transactional service under transactional services tab in "Manage Services" 
3. You will see the respective tracking ID in your transactional service details page as shown below

![Screenshot 2019-05-31 at 1 31 39 PM](https://user-images.githubusercontent.com/43952553/58684004-25777780-8366-11e9-9f99-90d7422e9a69.png)

## Examples

The code snippets below are just some example on how to call `startTransactionalService()` and `completeTransactionalService()` functions by using your assigned [Tracking Id](). You don't necessarily have to follow the example below.

!!! success "Onload-Event - Invoking `startTransactionalService()` and `completeTransactionalService()`"

```markup
    <html>
    <head>
    ...
    <script src="https://assets.wogaa.sg/scripts/wogaa.js"></script>
    </head>
    ...
    <script type="text/javascript">
        window.wogaaCustom.startTransactionalService('<trackingId>');
        window.wogaaCustom.completeTransactionalService('<trackingId>');
    </script>
    </html>
```

!!! success "On-click Event - Invoking `startTransactionalService()` and `completeTransactionalService()`"

```markup
    <html>
    <head>
    ...
    <script src="https://assets.wogaa.sg/scripts/wogaa.js"></script>
    </head>
    ...
    <!-- On-click event to start the transaction -->
    <button onclick="window.wogaaCustom.startTransactionalService('<trackingId>')">Start Transaction</button>
    ...
    <!-- On-click event to complete the transaction -->
    <button onclick="window.wogaaCustom.completeTransactionalService('<trackingId>')">Submit Transaction</button>
    </html>
```

In addition, some of the Transactional Service's designs of the system can have different ways at which the user starts and/or completes the transaction. For example:

* Invoking _onclick event_ for `startTransactionalService()` and  _onload event_ for `completeTransactionalService()`

If you have a button to indicate the start of the transaction, then you can put the `startTransactionalService()` on the _onclick Event_. For the complete transaction, if the user completes the transaction with a confirmation or "thank you" message page, then you need to add the `completeTransactionalService` on the _onload Event_ at the page.

## 

