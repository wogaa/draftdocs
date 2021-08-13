# Informational Service Common Questions

If your verification is not working after you have installed the Tracking Code and waited for more than 24 hours, there are a few reasons this could be happening. Below are the common issues and how to resolve them.

* **The Tracking Code was added incorrectly**

  It might be the case that you're using the staging tracking code in your production environment/site or vice versa, as such no data/event is detected in the correct collector in our WOGAA backend server.

  **Solution**: To find out if you've implemented the Tracking Code properly in the correct environment, refer to instructions for the [different environments]().

  Additionally, you can use your browser developer tools \(e.g. [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/open)\) to troubleshoot, right-click the page and select **Inspect** to see if there is/are any errors in the developer console.

* **No traffic to your Site**

  WOGAA verified tracking as being active if it detects at least one visit/event in the past hour. If your site hasn't had any visitors within the past hour\(s\),this could be due to low traffic to your site or perhaps your site's **Content Security Policy\(s\) is blocking the WOGAA Tracking Code**.

  **Solution**: If you suspect that the latter might be the issue, you need to whitelist your site's CSP rules. Refer to the [different environments]() for the CSP configurations.

## Still unable to get your Tracking Code to work?

No worries, WOGAA Support Team can help! You can reach out to us at wogaa@tech.gov.sg. We will response to you as soon as possible.

