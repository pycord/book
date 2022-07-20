# Coding a HTTP only bot
This section outlines the basics on how you are able to create a http-only bot application in Pycord.

## Provisions
Pycord provisions you basic tools to create a bot application which does not require the gateway,
this chapter of the book has extensive use of RESTApp which is Pycord's base class for REST-only Applications.

You can subclass this class for better extensibility and to make further development on your part easier.

## Caching
Pycord's Cache is also enabled on RESTApp, meaning you can run another app to provision its caching and other things.

This also gives you a one-fetch policy, which lets you discard making a request for going into the cache.
Although, after long periods of time this cache can get outdated since its working without a gateway,
so we ensure you use it lightly.

### Replacing Caches
Pycord lets you replace where you want to store your cache, all you have to do is subclass AsyncDict and enter it into state,
like so:

```py
from pycord.state import AsyncDict

class MyAsyncDict(AsyncDict):
    async def get(self, t: Any):
        return await self.my_db.get(t)

    async def pop(self, t: Any):
        return await self.my_db.pop(t)
```

and so on for other functions required.

