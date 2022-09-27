# Kafka Example KEBDI

## Requirements:

- `docker` installed
- `docker-compose` installed
- `plumber` installed

## 1. Installation

### On *Arch* Linux

In a terminal emulator run `sudo pacman -S docker docker-compose plumber` to install
all requirements.

### On *Ubuntu* (*Debian*) Linux

(Not tested)
In a terminal emulator run `sudo apt install docker docker-compose plumber` to install
all requirements.

### On *MacOS*

(Not tested)
In a terminal emulator run `brew tap batchcorp/public`, then `brew install docker docker-compose plumber`.

### On Windows Or manual install

Consult the [Official Docker Website](https://www.docker.com/) and [Plumber on Github](https://github.com/batchcorp/plumber).


## 2. Startup

Run `docker-compose up -d` in this folder. Wait until all 3 tasks ended successfully.

## 3. Playing with it

**Plumber** is a CLI tool that allows you to communicate with the kafta server running now in a 
Docker container on your PC.

To read messages from the server, run `plumber read kafka --address=localhost:29092 --topics <topic-name>`.
To write messages to the server, run `plumber write kafka --address=localhost:29092 --topics <topic-name> --input <data>`.

My suggestion: Open two terminal emulators and put them next to each other. In the right one,
run `plumber read --address=localhost:29092 --topics test -f`. The `-f` option tells plumber
to keep the connection open and keep listening to more incoming messages on that topic.
In the left terminal, you can now send messages (provider) to the kafka server on topic `test` and see
the values arrive in the right terminal (consumer).

Now you can test how kafka works, for example try to send multiple entries `--input-as-json-array`,
or open more terminal emulator windows to add providers and consumers, or use two topics at the 
same time.

## 4. Shutdown

Run `docker-compose down` in this folder.
