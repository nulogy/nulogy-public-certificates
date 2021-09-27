# Nulogy Public x509 Certificates
> Updated August 2016

## Introduction

Nulogy has developed a set of self-signed x509 certificates in a hierarchy of trust with an airgapped root authority and secure intermediate.

When deployed properly by administrators, these assets can reduce operational and security risks as well as administrator costs.

These certificates allow Secure FTP, AS2 and HTTPS communications with Nulogy's environment to be encrypted and authenticated.

NOTE: [Freestart collisions have been found for the SHA-1 hashing function.](https://sites.google.com/site/itstheshappening/) Do not use the provided SHA-1 certificates if your systems support the superior SHA-256. Nulogy Corporation is not responsible for security risks resulting from your choice to use our SHA-1 certificates. SHA-1 certificates are provided to facilitate your migration to secure services before SHA-1 is sunset permanently.

## Choosing a Certificate to Use


Which certificate you choose to install in your trust store is up to you, but you should prefer to install the highest certificate in the chain: the Nulogy Root CA4. This will significantly reduce the need for future configuration changes.

If your client software does not support trusted roots with provided intermediates, you may opt to install 001-issuing-ca-i4.crt.
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

It is your responsibility to validate the authenticity of the Nulogy Root certificate you trust. 
Failing to do so may void your customer agreements and leave you vulnerable to Man in The Middle (MitM) attacks.
Your Nulogy support representative will be able to help you validate the certificate key's fingerprint over the phone, via Mail, or another acceptable channel.

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
- ~~~100-axway.nulogy.net-geotrust-sha256.crt~~~ - EXPIRED B2Bi Production Environment Certificate, with SHA-256 Signatures by Geotrust
- 101-axway.nulogy.net-geotrust-sha256.crt -  B2Bi Production Environment Certificate, with SHA-256 Signatures by Geotrust
 - `1.3.6.1.4.1.311.60.2.1.3=CA/1.3.6.1.4.1.311.60.2.1.2=Ontario, C=CA, ST=Ontario, L=Toronto/businessCategory=Private Organization/serialNumber=2018280, O=Nulogy Corporation, OU=Infrastructure, CN=axway.nulogy.net`
- 102-cpi-https.nulogy.net-geotrust-sha256.crt - Shim interchange certificate

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

### 101-axway.nulogy.net-geotrust-sha256.crt

- This certificate is signed by Geotrust EV, to comply with some customer's requests that our SSL certificates be validated against our legal name.

### 102-cpi-https.nulogy.net-geotrust-sha256.crt - Shim interchange certificate

- Signed by Geotrust/RapidSSL, for data interchange.

### 201-connect.nulogy.net.crt

- Signed by Godaddy
- Extended Validation
- For use with b2bi 2.3

### 202-connect-na-qa.nulogy.net.crt

- Signed by Godaddy
- Extended Validation
- For use with b2bi 2.3

### 203-wildcard.nulogy.net.crt (new certificate)

- Signed by RapidSSL/Digicert
- For use with b2bi 2.3

Chain:
- Intermediate: RapidSSL RSA CA 2018 - (https://knowledge.rapidssl.com/support/ssl-certificate-support/index?page=content&actp=CROSSLINK&id=AR1548#lightbox-01)
- Root: DigiCert Global Root CA - (https://knowledge.rapidssl.com/support/ssl-certificate-support/index?page=content&actp=CROSSLINK&id=AR1548#lightbox-02)

### 204-connect.nulogy.net-i4-sha256.crt (expired)

- These are our connect.nulogy.net server side certificates for the production environment.
- We may be forced to revoke and re-issue these certificates in future due to configuration changes or security requirements.

### 205-connect-na-qa.nulogy.net-i4-sha256.crt (valid through April 27th 2022)

- These are our connect-na-qa.nulogy.net server side certificates for the QA/UAT environment.
- We may be forced to revoke and re-issue these certificates in future due to configuration changes or security requirements.

### 207-connect.nulogy.net.crt (valid through Sept 21st 2022)

- These are our connect.nulogy.net server side certificates for the production environment.
- We may be forced to revoke and re-issue these certificates in future due to configuration changes or security requirements.

### Copyright

The material in this repo is provided Copyright Nulogy Corporation 2016 - All Rights Reserved

Nulogy customers in good standing are licensed to use these x509 certificates only for connecting to Nulogy Corporation assets as prescribed by our standard operating procedures and by support instructions.
