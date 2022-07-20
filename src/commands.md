# Commands
Pycord's Implementation of commands is made to be more extensible, and more modular.

Its core design is class-based and based on multiple principles:

- Speed
- Modularity, Extensibility & Replacability
- Easiness

To put all of these in practice, the following system has been proposed.

## The System
Pycord's Command system works pretty simple, it will leverage multiple things like classes and subclasses,
putting it together can give the following example:

```py
import pycord
from pycord.commands import SlashCommand, Meta

# make a GatewayApp with an intent value of 0
app = pycord.GatewayApp(0)

# NOTE: The default type of command is SlashCommand
@app.command('echo')
async def echo(
    cmd: SlashCommand,
    content: pycord.Annotated[
        str,
        Meta(
            name='content',
            description='The content to echo!'
        )
    ]
):
    # responds to the command with its options' value
    await cmd.respond(content.value)

app.connect('token')
```

The `app.command` statement here initiates the command, you can enter a custom command class in the `cls`
parameter, which allows you to add much more customizations.
The `cmd` represents the command you just invoked, and should be the same class as `cls`,
the `content` fully represents the option you placed above, it also has an extra `[str]` type hint to represent it's value is a string.

You can also add a command like the following:

> NOTE: This could be redone at a point

```py
app.add_command(
    'echo',
    echo
)
```


### Explanation
To explain more, lets go through our arguments and parameters:

**arguments:**
- `'echo'` this is the name of the command, which will be given to the class.

**parameters:**
- `cmd` an instance of `cls`, in this case `SlashCommand`
- `content` the option which you want entered

There will also be other arguments that can be placed:

**arguments:**
- `cls` a custom command class to use
- `guild` a singular guild to limit this command onto
- `guilds` a list of guilds to limit this command to
- `guild_id` a singular guild to limit this command onto
- `guild_ids` a list of guilds to limit this command to
- `before` a list of functions to call before the command function is invoked
- `after` a list of functions to call after the command function is invoked
