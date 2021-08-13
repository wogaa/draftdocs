# Transactional Service Common Questions

## FAQs for TS Tracking Code Implementation & Verification

### `startTransactionalService()` is called, but why do I not see any Snowplow events fired?

Assuming you have [implemented]() and [verified]() the Event trigger codes correctly, the `startTransactionalService()` will only send events on the first call in a session. This is to prevent multiple counts of start if user keeps refreshing the page.

## Still unable to get your Tracking Code to work?

No worries, WOGAA Support Team can help! You can reach out to us at wogaa@tech.gov.sg. We will response to you as soon as possible.

