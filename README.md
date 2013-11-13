Generate Secure Shell Fingerprint DNS Resource Records
======================================================

Usage:

    ./sshfpgen

## Summary

This is a small shell script that uses commonly available utilities
to generate textual representations of SSHFP RRs from the host keys
on the current host. Copy and paste the output into your own BIND
zone file.

## Background

Read [RFC 4255](https://tools.ietf.org/html/rfc4255 "Using DNS to Securely Publish SSH Key Fingerprints"),
[RFC 6594](https://tools.ietf.org/html/rfc6594 "Use of the SHA-256 Algorithm with RSA, DSA, and ECDSA in SSHFP Resource Records"),
and the [IANA registry for applicable parameters](https://www.iana.org/assignments/dns-sshfp-rr-parameters/dns-sshfp-rr-parameters.xhtml "DNS SSHFP Resource Record Parameters")
for all you could ever want to know about this DNS RR type.

## Requirements and assumptions

This script depends upon

*   OpenSSL --- Provides cryptographic hash (message digest) computation
*   xxd --- Converts between binary and hexidecimal encoding

Per the OpenSSH convention, this script will seek the following files as input:

    /etc/ssh/ssh_host_rsa_key.pub
    /etc/ssh/ssh_host_dsa_key.pub
    /etc/ssh/ssh_host_ecdsa_key.pub

Future versions (patches accepted) may permit command line arguments to generate
specific record types for arbitrary SSH keys.
