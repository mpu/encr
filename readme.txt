ENCR(1)                   BSD General Commands Manual                  ENCR(1)

NAME
     encr — encrypt, authenticate and decrypt streams of data using a shared
     key.

SYNOPSIS
     encr [-g] [-d] [-k keyfile]

DESCRIPTION
     encr encrypts or authenticates and decrypts (with -d) using a shared
     96-bit key keyfile (provided via -k). Input is passed via stdin, and out‐
     put is printed to stdout.  encr generates keyfile with the -g flag.

     encr protects confidentiality with AES-256 CTR encryption, and checks
     integrity and authenticity using HMAC with the SHA256 hash function.
     encr will not pass unauthenticated data to stdout, and aborts when given
     an unauthenticated, reordered or truncated data stream.

     encr aborts if keyfile is world accessible.

EXIT STATUS
     The encr utility exits 0 on success, and >0 if an error occurs.

EXAMPLE
     generate a random key file:
     $ encr -g -k ./secret.key

     encrypt a plain text:
     $ encr -k ./secret.key < plain.txt > cipher.txt

     decrypt a cipher text:
     $ encr -d -k ./key.secret < cipher.txt > plain.txt


BSD                             March 17, 2017                             BSD