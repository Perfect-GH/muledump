##  Important Changes from Upstream Muledump

Muledump has traditionally used Yahoo's YQL service to process account data. This no longer working as Deca rate limits IPs blocking those requests.

This version of Muledump removes YQL and replaces it with the less graceful direct request.

#### Why is this "less graceful"?

In a nutshell, browsers don't like it when a website requests a URL to another website via Javascript. Yahoo YQL explicitly approves this sort of request, so it is fine. But ROTMG's servers do not.

In order to use this version of Muledump you need to be using Chrome with [this extension](https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi) to disable CORS. This extension when enabled will disable this security feature to enable Muledump to work. 

Just don't forget to configure it properly!

## Account Load Rate Limiting

Deca servers will now block you for 10 minutes if you make too many requests at once. Users with many accounts are finding themselves unable to use Muledump because of this.

This version of Muledump now rate limits how fast you hit Deca's servers in an attempt to prevent you getting blocked. You can fine-tune this setting by adding/changing in accounts.js:

```
accountLoadDelay = 5
```

In this example, and by default, there is a 5-second delay between loading each account. Setting to 0 will disable the limiter.