# Stack trace
If Dino crashes, a stack trace can be obtained by executing Dino within gdb. Make sure you have debug symbols installed.
```
gdb dino
> r // Starts dino 
[Do whatever makes Dino crash]
> bt // To obtain the stack trace
```
To get traces of runtime criticals, use `gdb dino --g-fatal-warnings`.

# Debug output
Additional output will be printed when `G_MESSAGES_DEBUG` is set to one or more values of: `libdino`, `omemo`

`env G_MESSAGES_DEBUG=libdino,omemo dino`

# View XML stanzas
Starting `dino` with `--print-xmpp=[filter]` results in stanzas being printed to stdout. You can create complex filters to specify which stanzas should be printed.

|`--print-xmpp=`                | Result      |
|------------------------------ | ----------- |
| `all`                         | All stanzas |
| `message`                     | Message stanzas |
| `message.body`                | Message stanzas with a `body` child node |
| `message[to=jid@example.com]` | Message stanzas with the `to` attribute set to `jid@example.com` |
| `presence.{jabber:x:signed}:x` | Presence stanzas having a child node `x` with namespace `jabber:x:signed`|
| `message\|iq`                  | Message and Iq stanzas |