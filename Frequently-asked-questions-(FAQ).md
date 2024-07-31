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

# How to change the nickname after having joined a room?

Send the following message to the room where you replace `[nickname]` with your desired nickname:

```
/nick [nickname]
```

# Which slash commands are supported?

Currently, there's no easily readable documentation for the commands that start with `/`.
They have to be looked up in the source code.

They can be found in the method for sending text in the chat input controller class.
For easier reference in case the code changes, [this is a link to the code at the time of writing this FAQ entry](https://github.com/dino/dino/blob/bf9f401743eb5bd9b2de2bcac56576a6454b290c/main/src/ui/chat_input/chat_input_controller.vala#L146) and [this is a link to the current version of the code](https://github.com/dino/dino/blob/master/main/src/ui/chat_input/chat_input_controller.vala#L146).

# How to add someone to my contact list?

Click on the _+_ button on the top left and select _Start conversation_. The list of contacts you see in the appearing dialog is also sometimes referred to as your roster. You can add someone to your contact list with the _+_ button at the bottom of the list and remove someone with the _-_ button.

# How to change the font size in Dino?

Dino adheres to the font size defined in the global GTK settings, so it could be changed there.

To scale the fonts only for Dino, the `GDK_DPI_SCALE` environment variable can be set before launching. For example, the terminal command for a larger font size is as follows on Ubuntu:
```shell
GDK_DPI_SCALE=1.5 dino
```

Another, more flexible solution in Dino 0.4 or later is to create or edit the file `~/.config/gtk-4.0/gtk.css`, or `~/.var/app/im.dino.Dino/config/gtk-4.0/gtk.css` in the Flatpak version, like that:
```css
@import 'colors.css';
window.dino-main {
  font-size: 18px;
}

window.dino-main .dino-conversation {
  font-size: 25px;
}
```

Note that this allows to adapt many other aspects of the design. For example, the following adapts the message spacing:
```css
@import 'colors.css';
window.dino-main .dino-conversation .message-box {
    padding: 3px 15px 3px 15px;
}
window.dino-main .dino-conversation .has-skeleton {
    margin-top: 10px;
}
window.dino-main .dino-conversation .message-box:not(.has-skeleton) {
    padding-left: 58px;
}
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

# How to set a dark theme?

Prefix the command to launch Dino, `dino` in this example, as follows:
```bash
GTK_THEME=Adwaita-dark dino
```

You would typically do this via the menu editor or directly in the `.desktop` file for Dino by editing the `Exec=` line accordingly to:

```.desktop
EXEC=env GTK_THEME=Adwaita-dark dino %U
```

This will apply the dark theme to Dino only and should work for any Dino and GTK version.

If you're using Dino 0.4 or later and GTK4 earlier than 4.11.4, you can execute the following command to apply the dark theme system-wide:

```bash
gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'
```

If you're using Dino 0.3 or earlier, add the following entry to `~/.config/gtk-3.0/settings.ini`:

```ini
[Settings]
gtk-application-prefer-dark-theme = true
```