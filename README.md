# Capture The Flag Challenge for eBPF Summit 2023

Welcome to the eBPF Summit 2023 CTF Challenge!

## Deploying the challenge

* On Mac, you can set up the challenge using Lima-VM by running `limactl start
  lima/<easy/hard>.yaml` with the file provided in this repo. Once this
  completes, open a shell into the VM with `limactl shell <easy/hard>`.

* If you're a Vagrant user, we've supplied a Vagrantfile for you as well.
  Download that file and run `vagrant up`. Once this is finished, run `vagrant
  ssh` to open a shell into the VM.

If you don't want to use Lima or Vagrant, you should be able to run the binary
`bin/ebpf.summit.2023` on a relatively modern Linux distro (as long as the
kernel is 5.15+).

# The premise!

Once your system is up and running you will be able to log into a running
Ubuntu machine!

However you'll notice that within the root directory is a file `/ebpf.summit`,
if you `sudo cat` this file you'll see that there is a program updating this
file, this hidden program is also systematically reading `/etc/passwd`. A
nefarious user (me) has hidden a userland program with eBPF, you'll need to use
whatever tools are at your disposal to locate this program and its pid in order
to kill (don't -9 the pid) the program. Only then will the `/ebpf.summit`
reveal the flag!

Good luck!

Check your answer or get hints at https://isogo.to/summit-2022-ctf-3.
