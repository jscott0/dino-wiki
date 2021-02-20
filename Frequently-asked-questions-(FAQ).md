# How to create a group chat?

*We plan to introduce dialogs to conveniently create channels and groups. The new UI will obsolete the following (more involved) steps.*

Click on the _+_ button on the top left and select _Join channel_. After clicking on the _+_ button below the channel list, the room address has to be provided in the _JID_ field. It has the form "_[room identifier]_@_[domain name]_".

The room identifier can be freely chosen, but it must not exist yet and must not contain spaces (hyphens or underscores are fine). The domain name that is used for rooms (also called <abbr title="Multi-User Chat">MUC</abbr>) depends on your server provider. Often, it can be found on the provider's website.

Once created, the room can be configured via the ☰ / ⚙ button on the top right.

## Configuring a private group

If you want the group chat to become a private group, you should configure it as: Persistent: `Yes`, Publicly searchable: `No`,  Members only: `Yes`, "Permission to view JIDs: `Anyone`

## Configuring a public channel

A public channel should be configured as: Persistent: `Yes`, Publicly searchable: `Yes`, Members only: `No`, Permission to view JIDs: `Moderators only`

# How to add someone to my contact list?

Click on the _+_ button on the top left and select _Start conversation_. The list of contacts you see in the appearing dialog is also sometimes referred to as your roster. You can add someone to your contact list with the _+_ button at the bottom of the list and remove someone with the _-_ button.

# How to change the font size in Dino?

Dino adheres to the font size defined in the global GTK settings, so it could be changed there.

To scale the fonts only for Dino, the `GDK_DPI_SCALE` environment variable can be set before launching. For example, the terminal command for a larger font size is as follows on Ubuntu:
```shell
GDK_DPI_SCALE=1.5 dino
```

# How to use Dino over Tor?

See the [related wiki page](https://github.com/dino/dino/wiki/Tor).

# How to run a second Dino instance

```
env DBUS_SESSION_BUS_ADDRESS=  XDG_DATA_HOME=/some/path dino
```