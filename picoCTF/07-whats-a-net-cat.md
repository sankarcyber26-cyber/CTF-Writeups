# What's a net cat? - picoCTF

## Category: General Skills
## Difficulty: Easy

## Description
Connect to a remote server using netcat to retrieve the flag.

## Approach

1. Used netcat to connect to the given server and port:
   $ nc fickle-tempest.picoctf.net 50097

2. Server sent the flag directly upon connection.

## Learning
- netcat (nc) is a simple but powerful tool to create raw 
  TCP/UDP connections to a server
- Many CTF challenges use nc to interact with remote 
  services and retrieve flags or data

## Flag
[Solved ✅ - try connecting yourself with nc!]
