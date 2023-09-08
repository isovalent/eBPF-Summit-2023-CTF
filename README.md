# Capture The Flag Challenge for eBPF Summit 2023

Welcome to the eBPF Summit 2023 CTF Challenge!

## Backstory

The backstory continues from the previous challenges. [You can find the
previous pieces here][previously]. Like for previous years, the story is here
for the atmosphere and does **not** contain hints to help solve the challenge.

> What a week.
>
> You are Jephen'Tsa. Hero of the Rebel Alliance, you've left behind your quiet
> life as a giant-bee-keeper on planet Berpafyll to fight against the Empire.
> Three days ago you got reconnected with your former ally, Blue Hex. She had
> apparently crossed you, but only to expose a spy at the heart of the command.
>
> He is Bajeroff Lake. Native from Rekkana, he's been in charge of computer
> systems and droids for the Rebellion over the last six years. All this time,
> he's also been covering his stakes in a megacorporation under Imperial
> control. More recently, he started to leak precious data to your foes. He's
> the spy identified by Blue Hex, and as soon as you came back to your base,
> two days ago, you exposed him.
>
> Mon Mothma, leader of the Alliance, immediately ordered that the traitor be
> arrested. Bajeroff resisted and locked himself in a server room, along with a
> bunch of droids under his command. You spent most of your day yesterday
> trying to drive him out. After many blasts, various subterfuges, a tea break,
> two lightsaber fights, and several other heroic actions, your team eventually
> managed to catch the spy alive and put him behind bars.
>
> But you're not out of the asteroid field yet. This morning, Blue Hex just
> realised that Bajeroff managed to infect all computers with clandestine
> malware. You're now logging into the system to try and find the malicious
> process to stop it. You'd better be quick, or the virus will send the
> position of your base to the Empire. Once again, everyone relies on you, and
> it's only Wednesday! May the Force be with you: you'll need it.

[previously]: https://gist.github.com/qmonnet/09afdd12a65ce3e5612d554b23246d76

## Deploying the challenge

* On Mac, you can set up the challenge using Lima-VM by running:

  ```
  limactl start lima/<easy/hard>.yaml
  ```

  with the file provided in this repo. Once this
  completes, open a shell into the VM with:

  ```
  limactl shell <easy/hard>
  ```

* If you're a Vagrant user, we've supplied a Vagrantfile for you as well.
  Download that file and run:

  ```
  vagrant up
  ```

  Once this is finished, run:

  ```
  vagrant ssh
  ```

  to open a shell into the VM.

If you don't want to use Lima or Vagrant, you should be able to run the binary
`bin/ebpf.summit.2023` as root on a relatively modern Linux distro (as long as
the kernel is 5.15+).

## The premise!

Once your system is up and running you will be able to log into a running
Ubuntu machine!

However you'll notice that within the root directory is a file `/ebpf.summit`,
if you `sudo cat` this file you'll see that there is a program updating this
file, this hidden program is also systematically reading `/etc/passwd`. A
nefarious user (me) has hidden a userland program with eBPF, you'll need to use
whatever tools are at your disposal to locate this program and its pid in order
to kill the program. Only then will the `/ebpf.summit` reveal the flag!

> **Warning**
>
> When killing the process, do not send `SIGKILL` (do not pass the `-9` option
> to `kill`), or the process will not have the opportunity to write its flag
> before closing.

Good luck!

Check your answer or get hints at `#ebpf-summit-ctf-spoilers` on the eBPF 
slack instance!

![Join the Cilium slack channel](https://img.shields.io/badge/slack-cilium-brightgreen.svg?logo=slack)
