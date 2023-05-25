# Nulogy Public x509 Certificates

> Updated August, 2022

## Introduction

Nulogy has developed a set of self-signed x509 certificates in a hierarchy of trust with an airgapped root authority and secure intermediate.

When deployed properly by administrators, these assets can reduce operational and security risks as well as administrator costs.

These certificates allow Secure FTP, AS2 and HTTPS communications with Nulogy's environment to be encrypted and authenticated.

NOTE: [Freestart collisions have been found for the SHA-1 hashing function.](https://sites.google.com/site/itstheshappening/) Do not use the provided SHA-1 certificates if your systems support the superior SHA-256. Nulogy Corporation is not responsible for security risks resulting from your choice to use our SHA-1 certificates. SHA-1 certificates are provided to facilitate your migration to secure services before SHA-1 is sunset permanently.

## Choosing a Certificate to Use

Which certificate you choose to install in your trust store is up to you, but you should prefer to install the highest certificate in the chain: the Nulogy Root CA4 / DigiCert Global Root CA. This will significantly reduce the need for future configuration changes.

If your client software does not support trusted roots with provided intermediates, you may opt to install 001-issuing-ca-i4.crt (the intermediate certificate).
The likelihood that we will have to revoke 001-issuing-ca-i4 and issue a replacement is low.

If your client software, or your internal processes do not allow you to use trusted Root certificates such as our CA4 or I4, you may wish to trust one of our server-side certificates directly.

If you choose to do so, note: the likelihood that we will have to revoke and reissue this certificate within the coming years is very high. If this occurs, and you do not include I4 or CA4 in your trust store, your applications will fail to communicate with our servers. We will give as much notice as possible for this, but for security reasons we may be forced to revoke this certificate immediately, without notice.

## Scheduled Expiry Dates

Please check the expiry date on the certificate you install. To do so, you may wish to use the OpenSSL utility included with most Unix-like operating systems:

```
$ openssl x509 -text -noout -in 000-root-ca4.crt
 ...
        Validity
            Not Before: Oct  7 10:48:37 2015 GMT
            Not After : Oct  6 10:48:37 2025 GMT
        Subject: C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Infrastructure, CN=Nulogy Root CA 4
 ...
```

In the case of certificates with shorter expiry, you may wish to add a calendar event to remind you prior to the date.

## Validating the Root Certificate

It is your responsibility to validate the authenticity of the Root certificate you trust.
Failing to do so may void your customer agreements and leave you vulnerable to Man in The Middle (MitM) attacks.
Your Nulogy support representative will be able to help you validate the certificate key's fingerprint over the phone, via Mail, or another acceptable channel.

## Contents

The files contained in this repository are as follows.


#### 000-root-ca4.crt - The Nulogy Root CA4 Certificate

- `C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Infrastructure, CN=Nulogy Root CA 4`
- Expires October 2025

- This is the current Nulogy Root CA Certificate.
- Extensive effort has been dedicated to utilising the very best practices for operating an Offline x509 Certificate Authority Root.
- The likelihood of this certificate being revoked or replaced before expiry is low.

#### 000-root-ca4.crt.signed.asc - A GPG Signature of 000-root-ca4.crt

- This is a signed copy of 000-root-ca4.crt.
  - Verify with 0xB52FEE3604963DD2 - for which proofs of ownership have been published.

#### 001-issuing-ca-i4.crt - The Nulogy Intermediate I4 Certificate

- `C=CA, O=Nulogy Corporation, OU=Infrastructure, CN=Nulogy Internal Issuing CA I4`
- Expires October 2025

- This is the current Nulogy Intermediate Certificate, used for day-to-day signings.
- In most cases we will combine this certificate with a server certificate and transmit it at the time a session is initiated.
  - Not all software supports this. In which case, you may elect to simply trust the I4 certificate as a trusted root, instead.
- The private key is stored securely and accessible only to a small number of vetted Infrastructure administrators.
- Extensive effort has been dedicated to utilising the very best practices for operating a private x509 Certificate Authority Root.
- The likelihood of this certificate being revoked or replaced in the near term is very low.

#### 220-connect.nulogy.net.crt - TLS Certificate Production

- `CN=connect.nulogy.net,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA, CN=DigiCert TLS RSA SHA256 2020 CA1,O=DigiCert Inc,C=US`
- Serial Number: 19733834873932870291682653328813255742 (0xed8992d796017602f6272079712ec3e)
- Contents include:
  - Certificate (connect.nulogy.net): Expiration **September 2023**
  - Intermediate Certificate (DigiCert TLS RSA SHA256 2020 CA1): Expiration April 2031
  - Root Certificate (DigiCert Global Root CA): Expiration November 2031
- Signed by Digicert
- These are our *connect.nulogy.net* server side certificates for the Production environment.
- For use with CNEDI and B2Bi Production


#### 221-connect-na-qa.nulogy.net.crt - TLS Certificate UAT

- `CN=connect-na-qa.nulogy.net,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA, CN=DigiCert TLS RSA SHA256 2020 CA1,O=DigiCert Inc,C=US`
- Serial Number: 5071367148915287984348724456423100702 (0x3d0b5b47a110ca7b21b04dff657111e)
- Contents include:
  - Certificate (connect-na-qa.nulogy.net): Expiration **February 2024**
  - Intermediate Certificate (DigiCert TLS RSA SHA256 2020 CA1): Expiration April 2031
  - Root Certificate (DigiCert Global Root CA): Expiration November 2031
- Signed by Digicert
- These are our *connect-na-qa.nulogy.net* server side certificates for the UAT environment.
- For use with CNEDI and B2Bi UAT

#### 301-connect-na-qa.nulogy.net.crt - AS2 signing/encryption UAT

- `CN=connect-na-qa.nulogy.net,OU=Integrations,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA`
- Serial Number: 17705727081225065378 (0xf5b760f8ae6f13a2)
- Expires April 2027

- This is our x.509 V3 5 year AS2 signing/encryption certificate.
- For use with CNEDI and B2Bi UAT


#### 302-connect.nulogy.net.crt - AS2 signing/encryption Production

- `CN=connect.nulogy.net,OU=Integrations,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA`
- Serial Number: 13992631575093187943 (0xc22fd0480a581567)
- Expires April 2027

- This is our x.509 V3 5 year AS2 signing/encryption certificate.
- For use with CNEDI and B2Bi Production



### Copyright

The material in this repo is provided Copyright Nulogy Corporation 2022 - All Rights Reserved

Nulogy customers in good standing are licensed to use these x509 certificates only for connecting to Nulogy Corporation assets as prescribed by our standard operating procedures and by support instructions.
