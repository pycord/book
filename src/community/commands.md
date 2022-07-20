# Prefix
The new prefixed system is supposed to be a better, more extensible system then the old
ext.commands extension.

## Making a simple prefixed commands
Pycord's prefix system is supposed to be easier then the old legacy system.
It is based on our standardized system and henceforth the following design is purposed:

```py
@app.command('hi', cls=prefix.Command, prefix='!')
async def hi(cmd: prefix.Command):
    await cmd.respond(f'hello {cmd.user.mention}!')
```

The design is short, and allows for different prefixes per-command.
The prefix argument also allows you to enter an asynchronous function to have access to things like per-guild prefixes.
