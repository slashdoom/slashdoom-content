---
title: A Simple Docker Image for Packet Captures
date: 2024-03-19
tags: ["docker", "pcap"]
draft: false
---

### A simple Alpine Linux based Docker image with tcpdump for network troubleshooting and testing

- The man page for tcpdump: http://www.tcpdump.org/tcpdump_man.html
- Docker Hub: https://hub.docker.com/repository/docker/slashdoom/tcpdump/general
- A GitHub repo with the Dockerfile: https://github.com/slashdoom/tcpdump-docker

### Run the Docker Image and Show the tcpdump Options
    docker run -it --rm slashdoom/tcpdump --help

### Usage
Packet capture another container to stdout:

    $ docker run -it --net container:[container name or ID]  slashdoom/tcpdump [TCPDUMP OPTIONS]

Packet capture another container to file:

    $ docker run -it -v $PWD:/pcap --net container:[container name or ID]  slashdoom/tcpdump -w /pcap/capture.pcap [TCPDUMP OPTIONS]


```goat
   .------------.            
   | Docker App |   .----.          .--------------.
   | Container  +--+ Intf |<------->| User Traffic |                                                           
   '------------'   '--+-'          '--------------'
                       |
                       |
                       |
                       v
                 .-----+-----.
                 |  tcpdump  |
                 | Container |
                 '-----------'

```