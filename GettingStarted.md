# Getting started #

This document describes the set of steps necessary to get a SleekBot up and running.

## Requirements ##

The following packages are required to run SleekBot

### Python 2.5 ###
SleekXMPP requires at least Python 2.5 so SleekBot does too.

### An XMPP account ###
The bot will also need an account to log into. Please be sure that the server you choose allows bots before creating an account there.

## Suggested Packages ##
The following packages, while not strictly required, will make running SleekBot more pleasant:
### TLSlite ###
TLSlite (http://trevp.net/tlslite/) is required for authentication on many servers.

### PythonDNS ###
You may need to specify your server in your config if you don't have PythonDNS.

### TCL/Tk ###
TCL and the Tkinter Python module are required to make use of the eggdrop plugin.

## Get the source ##

The source is available from the SVN repository at svn://netflint.net/sleekbot. To fetch it, run the following command:
```
svn co svn://netflint.net/sleekbot
```

## Configure the bot ##
An example configuration is provided in the file 'config-example.xml'. Start by copying this to some other file, such as 'config-mybot.xml'. Once you've got a config file, fire it up in your favourite text editor.

### XMPP account ###
The first thing you'll need is for your bot to be able to log in. Find the line (at the top) starting "<auth" and replace the 'jid' attribute with your bot's XMPP account, and the password ('pass' attribute) similarly. Unless you know otherwise you can remove the 'server' attribute and leave the 'priority' attribute as-is.

### MUC rooms ###
Next you'll probably want one or more rooms for the bot to join. These are specified beneath the "

&lt;rooms&gt;

" tag, in a "<muc" tag with attributes of 'room' and 'nick' to specify the muc room to join and the bot's chosen nick within that room respectively (the bot can have a different nick in each room if desired). Please check with the room owner(s) that it's acceptable to bring bots into their room before doing so, many people are hostile to alien bots in their channel.

### Plugins ###
All SleekBot features are provided by plugins. Plugins may have their own configuration requirements, but at the basic level to enable a plugin named 'uptime' the following would be put beneath the "

&lt;plugins&gt;



&lt;bot&gt;

" tags.
```
			<plugin name='uptime'>
				<config />
			</plugin>
```

### User Access ###
It's not required to set any users for the bot, but it's a good idea to at least add yourself as an owner.

#### Owners ####
Owners will, in the future, be able to perform tasks such as resetting the bot remotely, and any tasks for lower access levels.

#### Admins ####
Admins will, in the future, be able to perform tasks such as asking the bot to join channels and part them.

#### Members ####
Members are only needed if "

&lt;require-membership /&gt;

" is set, in which case they are not ignored by the bot.

#### Bans ####
Banned users will be ignored by the bot; this is useful for people who cause the bot to flood rooms.

If you want your bot to not reply to strangers, but only users that it knows, uncomment the "

&lt;require-membership /&gt;

" tag (most people won't want this).

## Running the bot ##
After configuring the bot, it can be run by calling (replace 'config-mybot.xml' as appropriate).
```
./sleekbot -c config-mybot.xml
```