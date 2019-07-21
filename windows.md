### Windows Subsystem for Linux (WSL)

### Cmder

### Xming

### X11 Forwarding

To get rid of the warning

"Warning: No xauth data; using fake authentication data for X11 forwarding."

Follow the instructions at

https://gist.github.com/DestinyOne/f236f71b9cdecd349507dfe90ebae776

If the problem persist,

run

`xauth generate :0 .`
