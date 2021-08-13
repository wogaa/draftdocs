---
description: How to Correlate Sentiments Data to Your Agency's Data
---

# Correlating Sentiments with agency’s data

## Optional: How to Correlate Sentiments Data to Your Agency's Data

!!! info If you’re looking at WOGAA Sentiments data you need to understand one thing: we do not collect any personally identifiable information other than the e-mail input field; except that it’s an optional field for the user to fill it in.

There are many times when an agency wants to get more information of their visitors to provide better services or support cases and in some cases both.

So what can you do? Sentiments now offers the ability to correlate your agency's data with Sentiments data through tagging of agency's **own unique identifier** \(for e.g. Transaction ID, Session ID, or others\) that is stored in your own database/server that can uniquely identify the visitor\(s\) or the transaction\(s\) performed on your website\(s\). To illustrate:

* Transaction ID - _for e.g. after a successful submission by a user, usually there will be a transaction ID that can be used to verify the ownership of the submitted transaction_.
* Session ID - _for e.g. a unique identifier that your website assigns to a specific user for some predetermined duration of time or session, to keep track of visitor activity such as the last state before the user drop off from your site_.

After you've defined and done the setup on your end, you will be able to associate it with the Sentiments data collected once a user submits his/her sentiments through your website\(s\). And in the following, we'll show you how to implement the unique identifier for each digital service\(s\) or in your page\(s\).

### For Informational Services

For pages that you would like to tag sentiments, just call the method `addMeta()` with the object `{"agencyTxnId": "<your_own_unique_identifier>"}`.

```text
<html>
<head>
<!-- WOGAA.js code -->
</head>
<body>
...
...
<script>
      /*
     * Once the Transaction ID has been retrieved e.g. from an API call,
     * pass the Transaction ID to the method below.
     *
    */

    window.wogaaCustom.addMeta({"agencyTxnId": "<your_own_unique_identifier>" });
</script>
</html>
```

### For Transactional Services

For Transactional Services, Sentiments will be triggered on the `completeTransactionalService()` call. As such, the `addMeta()` with the object `{"agencyTxnId": "<your_own_unique_identifier>"}` should be called before that.

```text
<html>
<head>
<!-- WOGAA.js code -->
</head>
<body>
...
...
<script>
    window.wogaaCustom.addMeta({"agencyTxnId": "<your_own_unique_identifier>" });
    // addMeta() must be called before completeTransactionalService()

    window.wogaaCustom.completeTransactionalService("<tracking_ID>");
    /*
    tracking_ID is given to you when you registered your Transaction Service(s)
    onto wogaa. For e.g tracking-123
    */
</script>
</html>
```

