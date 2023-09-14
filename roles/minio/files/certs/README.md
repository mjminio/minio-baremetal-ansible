# TLS Certs

This directory contains the TLS certificates and keys for the MinIO server. The certificates and keys should be named `public.crt` and `private.key` respectively. If you are using a CA self-signed certificate, add the CA certificate to the same directory and name it `ca.crt`.

- `public.crt`: The public certificate for the MinIO server. This should be the full certificate chain.
- `private.key`: The private key for the MinIO server.
- `ca.crt`: The CA certificate for the MinIO server. This is required if you are using a CA self-signed certificate.