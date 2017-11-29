View XML stanzas
================
Starting `dino` with `--print-xmpp=[filter]` results in stanzas being printed to stdout. You can create complex filters to specify which stanzas should be printed.

|`--print-xmpp=`                | Result      |
|------------------------------ | ----------- |
| `all`                         | All stanzas |
| `message`                     | Message stanzas |
| `message.body`                | Message stanzas with a `body` child node |
| `message[to=jid@example.com]` | Message stanzas with the `to` attribute set to `jid@example.com` |
| `presence.{jabber:x:signed}:x` | Presence stanzas having a child node `x` with namespace `jabber:x:signed`|
| `message\|iq`                  | Message and Iq stanzas |