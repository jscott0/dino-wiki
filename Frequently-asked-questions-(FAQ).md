# How to create a group chat?

*We plan to introduce dialogs to conveniently create channels and groups. The new UI will obsolete the following (more involved) steps.*

Click on the _+_ button on the top left and select _Join channel_. After clicking on the _+_ button below the channel list, the room address has to be provided in the _JID_ field. It has the form "_[room identifier]_@_[domain name]_".

The room identifier can be freely chosen, but it must not exist yet and must not contain spaces (hyphens or underscores are fine). The domain name that is used for rooms (also called <abbr title="Multi-User Chat">MUC</abbr>) depends on your server provider. Often, it can be found on the provider's website.

Once created, the room can be configured via the ☰ / ⚙ button on the top right. You can configure it to be a private group or a public channel by setting the following values:

| Setting name | Private Group | Public Channel |
|--------------|---------------|----------------|
| Persistent   | Yes           | Yes            |
| Publicly searchable | No | Yes |
| Members only | Yes | No |
| Permission to view JIDs | Anyone | Moderators only |

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

# How to run another separate Dino instance?

```shell
env DBUS_SESSION_BUS_ADDRESS=  XDG_DATA_HOME="${dino_folder_path_for_this_instance}" dino
```

# How to move the data and configuration?

**Warning: Wrongly copying Dino's data around leads to OMEMO not working anymore**

Dino's data contains Dino's OMEMO keys. An OMEMO key can only be used by *one* client. The per-client key changes with every exchanged message. That means
- You can't use the same OMEMO key on multiple devices. The protocol doesn't work that way. It *will* break.
- You shouldn't backup and restore an old state of the OMEMO keys, since the keys continuously change. It won't work.

What you can do is to **move** Dino from installation A to installation B. Dino's data and configuration is contained in the `~/.local/share/dino` folder. Quit Dino before moving the folder.

# Is it possible to hide Dino and show an icon in the system tray?

No, but it's planned. It will be probably realised by directly implementing the StatusNotifierItem D-Bus interface. Pull requests are welcome!

# Is it possible to enable OMEMO by default?

No, but we understand that improvements in that area are needed.

# How can I set a dark theme?

Add the following entry to `~/.config/gtk-3.0/settings.ini`:

```ini
[Settings]
gtk-application-prefer-dark-theme = true
```