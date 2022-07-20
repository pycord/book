# Extensions
Pycords' new extension design is created to be easier, more intuitive and faster for anyone and everyone.

The design is less class-based and more instance based.
An example which could be given is the following:

```py
from pycord.community import extensions

# creates an Extension with the name of `__name__`
extension = extensions.Extension(__name__)

@extension.listen('hook')
def on_hook():
    print('The bot is online!')
```

that example generates the hook event.

> Note: Functions like Listening and Commands will be the same
> as they are normally.

## Loading Extensions
To load an extension, you'll have to do something like the following:

```py
import pycord
from extensions.my_extension import extension

# initiate a GatewayApp instance with an intent value of 0
app = pycord.GatewayApp(0)

# loads the extension onto the app
# if you enter another extension here it extends it onto there.
extension.extend(app=app)

# connects to the Gateway
app.connect('token')
```
