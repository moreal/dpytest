# dpytest

This is a package to allow testing of discord.py.
It is only compatible with the rewrite version, and is still in early alpha.

# Usage

dpytest can be used for projects using the default commands.Bot, or those defining their own subclass of bot.
For someone using a custom class, code would look something like this:
```python
import discord.ext.test as dpytest
import yourbot


def test_bot():
    bot = yourbot.BotClass()
    
    # Load any extensions/cogs you want to in here
    
    dpytest.configure(bot)
    
    dpytest.message("!help")
    dpytest.verify_message("[Expected help output]")
```

The dpytest framework is designed to be used best with pytest style fixtures, but is technically framework agnostic.  
With pytest, the bot setup step would be moved into a fixture so each test could use that fixture. Configure will ensure
that all state is reset after each call.