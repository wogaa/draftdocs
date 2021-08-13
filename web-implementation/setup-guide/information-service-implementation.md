---
description: >-
  As a best practice, you should test the code on your staging environment
  before deploying it on your production environment.
---

# Information Service Implementation

{% tabs %}
{% tab title="Test Environment" %}
## Implement Code in Test Environment

Having the Test environment\(s\) setup successfully, allows our users such as the business owners and/or developers to test any existing or new enhancements that WOGAA pushes out or launches such as the Sentiments widget, widget designs and interactions, and etc, without worrying about it breaking their Live Environment\(Production\).

### Step 1. Register your Test Environment

* To register your test environment you will need to login to wogaa.sg
* Navigate to the specific Information Service under the `Manage Services` tab
* Select the `Test Environment` tab
* Select `Register Test Environment` to register your respective test environment's domain/URL

![Screenshot 2019-11-25 at 6 23 40 PM](https://user-images.githubusercontent.com/43952553/69532432-b4f49080-0f6d-11ea-94bb-7427c2168954.png)

* After registration, proceed to Step 2 to insert tracking code into your registered environment.

### Step 2. Insert Tracking Code

Click on **Copy to Clipboard** to insert the following Tracking Code into the `<head>` section of every page of your website, before other scripts.

```markup
<script src="https://assets.dcube.cloud/scripts/wogaa.js"></script>
```

**Example**

```markup
<html>
    <head>
        ...
        <script src="https://assets.dcube.cloud/scripts/wogaa.js"></script>
    </head>
    ...
</html>
```

!!! info The base code does not support subresource integrity \(SRI\). Please do not enable SRI for base code.

### Content Security Policies for Staging

!!! info This step is optional if your website doesn't have Content Security Policy enabled.

If your website has Content Security Policy enabled, update your CSP with the following code:

```text
default-src 'self' https://*.dcube.cloud/ https://*.demdex.net/ https://cm.everesttech.net/ https://wogadobeanalytics.sc.omtrdc.net/;
frame-src 'self' https://wogaa.demdex.net;
script-src 'self' blob: https://*.dcube.cloud https://assets.adobedtm.com/;
img-src 'self' data: https://wogadobeanalytics.sc.omtrdc.net/ https://cm.everesttech.net/ https://dpm.demdex.net/;
connect-src 'self' https://*.dcube.cloud https://dpm.demdex.net/;
style-src 'self' 'unsafe-inline' https://assets.dcube.cloud/fonts/;
font-src 'self' data: https://assets.dcube.cloud/fonts/;
```

### Step 3. Verify Test Environment\(s\) for e.g. Staging

{% page-ref page="../verification/informational-service-verification.md" %}
{% endtab %}

{% tab title="Production Environment" %}
## Implement Code in Production Environment

### Step 1. Insert Tracking Code

Insert the following code into the `<head>` of every page of your website, before other scripts.

```markup
<script src="https://assets.wogaa.sg/scripts/wogaa.js"></script>
```

**Example**

```markup
<html>
    <head>
        ...
        <script src="https://assets.wogaa.sg/scripts/wogaa.js"></script>
    </head>
    ...
</html>
```

!!! info The base code does not support subresource integrity \(SRI\). Please do not enable SRI for base code.

### Content Security Policies for Production

!!! info This step is optional if your website doesn't have Content Security Policy enabled.

If your website has Content Security Policy enabled, update your CSP with the following code:

```text
default-src 'self' https://*.wogaa.sg https://*.demdex.net/ https://cm.everesttech.net/ https://wogadobeanalytics.sc.omtrdc.net/;
frame-src 'self' https://wogaa.demdex.net;
script-src 'self' blob: https://*.wogaa.sg https://assets.adobedtm.com/;
img-src 'self' data: https://wogadobeanalytics.sc.omtrdc.net/ https://cm.everesttech.net/ https://dpm.demdex.net/;
connect-src 'self' https://*.wogaa.sg https://dpm.demdex.net/;
style-src 'self' 'unsafe-inline' https://assets.wogaa.sg/fonts/;
font-src 'self' data: https://assets.wogaa.sg/fonts/;
```

### Step 2. Verify Production Environment

{% page-ref page="../verification/informational-service-verification.md" %}

### Step 3. After WOGAA Tracking Code Installed 

You can start using any of WOGAA's features: Web Analytics, Uptime, Inspect, Sentiments, and [more](https://wogaa.sg/home/index.html#/).
{% endtab %}
{% endtabs %}



{% page-ref page="../../troubleshooting/informational-service-common-questions.md" %}



