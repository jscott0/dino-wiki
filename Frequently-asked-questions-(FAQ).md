# How to change the font size in Dino?

Dino adheres to the font size defined in the global GTK settings, so it could be changed there.

To scale the fonts only for Dino, the `GDK_DPI_SCALE` environment variable can be set before launching. For example, the terminal command for a larger font size is as follows on Ubuntu:
```shell
GDK_DPI_SCALE=1.5 dino-im
```

# How to hide Dino but keep it running?

Launch Dino with the `--gapplication-service` parameter to make it run in the background, e.g. like this on Ubuntu:
```shell
dino-im --gapplication-service
```
Then you can start Dino as usual and when you close the window, it will be just hidden while notifications still arrive.

Be aware that this feature is work in progress and still has some issues. A detailed discussion about [minimising to the system tray can be found in the related issue](https://github.com/dino/dino/issues/98).

# How to create a group chat?

Click on the _+_ button on the top left and select _Join channel_. After clicking on the _+_ button below the channel list, the room address has to be provided in the _JID_ field. It has the form "_[room identifier]_@_[domain name]_".

The room identifier can be freely chosen, but it must not exist yet and must not contain spaces (hyphens or underscores are fine). The domain name that is used for rooms (also called <abbr title="Multi-User Chats">MUC</abbr>) depends on your server provider. Often, it can be found on the provider's website.

Once created, the room can be configured via the _⚙_ button on the top right.

# How to use Dino over Tor?

See the [related wiki page](https://github.com/dino/dino/wiki/Tor).