# Vagga on Barge with Vagrant

[Vagga](http://vagga.readthedocs.io/en/latest/) is a containerization tool to create development environments without daemons unlike Docker.

This shows how to create a Vagga environment on [Barge](https://atlas.hashicorp.com/ailispaw/boxes/barge) with [Vagrant](https://www.vagrantup.com/) instantly.

## Requirements

- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)

## Boot up

```bash
$ vagrant up
```

That's it.

## Hello World

```bash
$ vagrant ssh
Welcome to Barge 2.1.2, Docker version 1.9.1, build 66c06d0-stripped
[bargee@barge ~]$ cd hello-world/
[bargee@barge hello-world]$ vagga
Available commands:
    run                 Run flask app
[bargee@barge hello-world]$ vagga run
.
.
.
 * Running on http://0.0.0.0:5000/
```

At an another terminal

```bash
$ open http://localhost:5000/
```
