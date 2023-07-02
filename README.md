# amidiminder
ALSA utility to keep your MIDI devices connected

### The problem

  * Using `aconnect` to reconnect your devices and your software gets old quick.
  * If you power cycle a synth... you've got to `aconnect` it again.
  * Bandmate "helps" by unplugging a USB cord to untanlge and plugs it in again:
    Now you're controller is disconnected.

### The solution

`amidiminder` is a program that runs as a service. It will:

  1. Reads a rules file of connections you'd like made.

  2. When the MIDI devices & software - `amidimider` will
     automatically connect them according to the rules.

  3. It also Watches any connections you make with `aconnect` or that your
     software makes, and remembers them too.

  4. If any MIDI port goes away (power cycle, pulled USB cord, etc..), ALSA
     will silentlly remove the connections...
     ... But when the MIDI port comes back - `amidimider`'s got your back and
     will connect them right back up again just as they were.


## Building

Prerequisites:
  *  g++-10 compiler
  * make
  * libasound2-dev

```sh
sudo apt install g++-10 make libasound2-dev
```

Clone this repo and run `make`:

```sh
git clone https://github.com/mzero/amidiminder.git
cd amidiminder

vi debian/control
Architecture: arm64

make CXX=g++-10 CC=g++-10
```

Outputs:

 - build executable is in `build/amidiminder`.
 - deb package is in `build/amidiminder.deb`.


## Install

Installing the built deb package will install a systemd service that runs
`amidiminder` at startup.

```sh
sudo dpkg -i build/amidiminder.deb
```

That's it. — It's installed. — It's running — You're done!

