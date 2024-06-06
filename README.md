# A certificate authority for local development instances

This directory contains the PEM-encoded certificate and private key
for a web server answering at the following host names:

* `localhost`
* `*.local`

It also contains the PEM-encoded certificate and private key of the
self-signed certificate authority which issued that certificate.


## Regenerating the certificate authority

If you want to recreate the PEM-encoded certificate and private key of
certificate authority, install
first [CFSSL](https://github.com/cloudflare/cfssl), and then run the
script `generate-ca`:

    $ ./generate-ca
    Creating self-signed CA ...
    2024/06/06 16:17:46 [INFO] generating a new CA key and certificate from CSR
    2024/06/06 16:17:46 [INFO] generate received request
    2024/06/06 16:17:46 [INFO] received CSR
    2024/06/06 16:17:46 [INFO] generating key: rsa-2048
    2024/06/06 16:17:47 [INFO] encoded CSR
    2024/06/06 16:17:47 [INFO] signed certificate with serial number 264429173302228558055650968473082554429674769157
    Verifying CA cert ...
    $ ls -l local-ca*.pem
    -rw------- 1 carlos users 1679 Jun  6 16:17 local-ca-key.pem
    -rw-r--r-- 1 carlos users 4245 Jun  6 16:17 local-ca.pem
	$


## Regenerating the host certificate

In a similar way, you may recreate the host certificate and private
key file with the script `generate-host`:

    $ ./generate-host
    Creating host TLS cert and key ...
    2024/06/06 16:19:21 [INFO] generate received request
    2024/06/06 16:19:21 [INFO] received CSR
    2024/06/06 16:19:21 [INFO] generating key: rsa-2048
    2024/06/06 16:19:21 [INFO] encoded CSR
    2024/06/06 16:19:21 [INFO] signed certificate with serial number 402337168809931488419837434136738839808173835579
    Verifying host cert ...
    $ ls -l host*.pem
    -rw------- 1 carlos users 1679 Jun  6 16:19 host-key.pem
    -rw-r--r-- 1 carlos users 4674 Jun  6 16:19 host.pem
    $
