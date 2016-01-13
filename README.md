# Nulogy Axway-Test environment x509 Certificates
> Published January 2016

## Introduction

Nulogy has developed a set of self-signed x509 certificates in a hierarchy of trust with an airgapped root authority and secure intermediate.

When deployed properly by administrators, these assets can reduce operational and security risks as well as administrator costs.

These certificates ensure Secure FTP, AS2 and HTTPS communications with Nulogy's environment are encrypted and authenticated.

NOTE: [Freestart collisions have been found for the SHA-1 hashing function.](https://sites.google.com/site/itstheshappening/) Do not use the provided SHA-1 certificates if your systems support the superior SHA-256 algorithm. Nulogy Corporation is not responsible for security risks resulting from your choice to use our SHA-1 certificates. SHA-1 certificates are provided to facilitate your migration to secure services before SHA-1 is sunset permanently.

## Which should I install?


Which certificate you choose to install in your trust store is up to you, but you should prefer to install the highest certificate in the chain: the Nulogy Root CA4. This will significantly reduce the need for future configuration changes.

If your client software does not support trusted roots with provided intermediates, you may opt to install 001-issuing-ca-i4.crt.
The likelihood that we will have to revoke 001-issuing-ca-i4 and issue a replacement is low.

If your client software, or your internal processes do not allow you to use trusted Root certificates such as our CA4 or I4, you may wish to trust one of our server-side certificates directly. 

If you choose to do so, note: the likelihood that we will have to revoke and reissue this certificate within the coming years is very high. If this occurs, and you do not include I4 or CA4 in your trust store, your applications will fail to communicate with our servers. We will give as much notice as possible for this, but for security reasons we may be forced to revoke this certificate immediately, without notice.

## Expiry Dates

Please check the expiry date on the certificate you install. 

You may wish to add a calendar event several months before the expiry, to ensure you are reminded of the requirement to rotate the certificate before it expires.

## Validating the Root Certificate

Either: 

- You may fetch https://nulogy.com/nulogy-root-ca4.crt - which is served over HTTPS, signed by our Nulogy.com wildcard from RapidSSL.

Or:

- Get nulogy-root-ca4.crt from http://ca4.nulogy.com
- Verify the GPG signature from our Infrastructure Team Lead, `Ian Penney <ianp@nulogy.com>`, using GPG Key `B52FEE3604963DD2`.

Further:

- A signature from GPG Key `B52FEE3604963DD2` has been published to DNS Text record, ianp.identity.nulogy.com, verifying that ianp has control over the Nulogy.com domain. A proof has also been published at https://nulogy.com/keybase.txt
- The GPG key is registered at https://keybase.io/ with a series of social proofs for validation.
- The GPG key used is also printed on the keyholder's business cards, if you have one.

Or:

- Contact your Nulogy support representative for manual confirmation of the key fingerprint.


## Contents

The files contained in this repository are as follows.

- 000-root-ca4.crt - The Nulogy Root CA4 Certificate
  - `C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Infrastructure, CN=Nulogy Root CA 4`
- 000-root-ca4.crt.signed.asc - A GPG Signature of 000-root-ca4.crt
- 001-issuing-ca-i4.crt - The Nulogy Intermediate I4 Certificate
  - `C=CA, O=Nulogy Corporation, OU=Infrastructure, CN=Nulogy Internal Issuing CA I4`
- 002-axway-test.nulogy.net-i4-sha1.crt - B2Bi Test Certificate, with SHA-1 Signatures by I4
  - `C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Integrations, CN=axway-test.nulogy.net`
- 003-axway-test.nulogy.net-i4-sha256.crt - B2Bi Test Certificate, with SHA-256 Signatures by I4
  - `C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Integrations, CN=axway-test.nulogy.net`
- 004-axway.nulogy.net-i4-sha1.crt - B2Bi Production Certificate, with SHA-1 Signatures by I4
  - `C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Integrations, CN=axway.nulogy.net`
- 005-axway.nulogy.net-i4-sha256.crt - B2Bi Production Certificate, with SHA-256 Signatures by I4
 - `C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Integrations, CN=axway.nulogy.net`
- 100-axway.nulogy.net-geotrust-sha256.crt - B2Bi Production Environment Certificate, with SHA-256 Signatures by Geotrust
 - `1.3.6.1.4.1.311.60.2.1.3=CA/1.3.6.1.4.1.311.60.2.1.2=Ontario/businessCategory=Private Organization/serialNumber=2018280, C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Infrastructure, CN=axway.nulogy.net`

### 000-root-ca4.crt

- This is the current Nulogy Root CA Certificate.
- Extensive effort has been dedicated to utilising the very best practices for operating an Offline x509 Certificate Authority Root.
- The likelihood of this certificate being revoked or replaced before expiry is low.


### 000-root-ca4.crt.signed.asc

- This is a signed copy of 000-root-ca4.crt. 
  - Verify with 0xB52FEE3604963DD2 - for which proofs of ownership have been published.

### 001-issuing-ca-i4.crt

- This is the current Nulogy Intermediate Certificate, used for day-to-day signings.
- In most cases we will combine this certificate with a server certificate and transmit it at the time a session is initiated.
  - Not all software supports this. In which case, you may elect to simply trust the I4 certificate as a trusted root, instead.
- The private key is stored securely and accessible only to a small number of vetted Infrastructure administrators.
- Extensive effort has been dedicated to utilising the very best practices for operating a private x509 Certificate Authority Root.
- The likelihood of this certificate being revoked or replaced in the near term is very low.

### 002-axway-test.nulogy.net-i4-sha1.crt / 003-axway-test.nulogy.net-i4-sha256.crt

- These are our axway-test.nulogy.net server side certificates for the test environment.
- This certificate has SubjectAlternativeNames (SANs) to ease future migrations.
- We may be forced to revoke and re-issue these certificates in future due to configuration changes or security requirements.

### 004-axway.nulogy.net-i4-sha1.crt / 005-axway.nulogy.net-i4-sha256.crt

- These are our axway.nulogy.net server side certificates for the production environment.
- This certificate has SubjectAlternativeNames (SANs) to ease future migrations.
- We may be forced to revoke and re-issue these certificates in future due to configuration changes or security requirements.

### 100-axway.nulogy.net-geotrust-sha256.crt

- This certificate is signed by Geotrust EV, to comply with some customer's requests that our SSL certificates be validated against our legal name.


### Copyright

The material in this repo is provided Copyright Nulogy Corporation 2016 - All Rights Reserved

Nulogy customers in good standing are licensed to use these x509 certificates only for connecting to Nulogy Corporation assets as prescribed by our standard operating procedures and by support instructions.
