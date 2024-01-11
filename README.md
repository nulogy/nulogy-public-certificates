# Nulogy Public x509 Certificates

> Updated Aug, 2023

## Introduction

Nulogy has a set of self-signed x509 certificates for AS2 and a set of TLS x509 certificates signed by [Digicert](https://www.digicert.com/kb/digicert-root-certificates.htm). 

When deployed properly by administrators, these assets can reduce operational and security risks as well as administrator costs.

These certificates allow Secure FTP, AS2 and HTTPS communications with Nulogy's environment to be encrypted and authenticated.

## Choosing a Certificate to Use

### AS2 Certificates

If you are connecting over HTTP with AS2, you have the following options for Production and UAT environments.
| Options  | Production  | UAT |
| - | ------------- | ------------- |
| | [302-connect.nulogy.net.crt](302-connect.nulogy.net.crt) | [301-connect-na-qa.nulogy.net.crt](301-connect-na-qa.nulogy.net.crt)|

---
### TLS Certificates

If you are connecting over HTTPS with SSL/TLS, you have the following options for Production and UAT environments.
| Options  | Production  | UAT |
| - | ------------- | ------------- |
| Root Certificate *(Preferred Option)*| [DigiCertGlobalRootG2.crt.pem](DigiCertGlobalRootG2.crt.pem) | [[DigiCertGlobalRootG2.crt.pem](DigiCertGlobalRootG2.crt.pem)   |
| Intermediate Certificate *(Alternative Option)* | DigiCert Intermediate G2 CA  | DigiCert Intermediate G2 CA  |
| Yearly Server Certificate *(Alternative Option)* | [222-connect.nulogy.net.crt](222-connect.nulogy.net.pem) | [223-connect-na-qa.nulogy.net.crt](223-connect-na-qa.nulogy.net.crt)|

Note: 

---
> #### Notes about TLS Certificate Options
>
> Notice: The Digicert Root CA has been replaced by the Digicert Root G2 for all certificates created after March 2023.
> 
> Which TLS certificate you choose to install in your trust store is up to you, however should prefer to install
> the highest certificate in the chain: the [DigiCert Global Root G2](#digicertglobalrootg2crtpem---tls-digicert-root-g2-certificate) certificate,
> this will significantly reduce the need for future configuration changes.
>
> If your client software does not support trusted roots with provided intermediates, you may opt to install the DigiCert Intermediate G2 CA certificate.
> The likelihood that we will have to change the intermediate cert and use a replacement is low.
>
> If your client software or your internal processes do not allow you to use trusted Root certificates, you can use the yearly server certificates.
> If you choose to do so, note that we will have to reissue this certificate yearly.
> When this occurs, if you do not include the intermediate or root certificates in your trust store, your applications will fail to communicate with our servers.
> We will give as much notice as possible for the yearly certificate reissue, but for security reasons we may be forced to revoke this certificate immediately, without notice.
> 

---
## Contents

The files contained in this repository are as follows:

#### [DigiCertGlobalRootG2.crt.pem](DigiCertGlobalRootG2.crt.pem) - TLS Digicert Root G2 Certificate 
- Mirror of [DigiCert Global Root G2](https://www.digicert.com/kb/digicert-root-certificates.htm#:~:text=03%3A3A%3AF1%3AE6%3AA7%3A11%3AA9%3AA0%3ABB%3A28%3A64%3AB1%3A1D%3A09%3AFA%3AE5), hosted here for convenience
- Serial Number: 4293743540046975378534879503202253541 (`0x33af1e6a711a9a0bb2864b11d09fae5`)
- Expires January 2038
- Currently for use with HTTPS/TLS connectivity to CNEDI and B2BI, for the Production environment


#### [223-connect-na-qa.nulogy.net.crt](223-connect-na-qa.nulogy.net.crt) - TLS Certificate for UAT Environment

- Subject:`CN=connect-na-qa.nulogy.net,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA` (Issuer: `CN=DigiCert TLS RSA SHA256 2020 CA1,O=DigiCert Inc,C=US`)
- Serial Number: 19806049027757082700868699962183856442 (`0xee6819c3cfb66e2ca5ff53e280d313a`)
- Expires **January 2025**
- Contents include:
  - Certificate (connect-na-qa.nulogy.net)
  - Intermediate CA Certificate (DigiCert Global G2 TLS RSA SHA256 2020 CA1)
  - Root CA Certificate ([DigiCert Global Root G2](#digicertglobalrootg2crtpem---tls-digicert-root-g2-certificate))
- Signed by Digicert
- This is the `connect-na-qa.nulogy.net` server side certificates for our UAT environment
- For use with CNEDI and B2Bi UAT

#### [222-connect.nulogy.net.crt](222-connect.nulogy.net.pem) - TLS Certificate for Production Environment

- Subject: `CN=connect.nulogy.net,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA` (Issuer: `CN=DigiCert Global G2 TLS RSA SHA256 2020 CA1,O=DigiCert Inc,C=US`)
- Serial Number: 9034213788272798128800337420850908347 (`0x6cbed211256807796478204ef054cbb`)
- Expires **August 2024**
- Contents include:
  - Certificate (connect.nulogy.net)
  - Intermediate G2 Certificate (DigiCert Global G2 TLS RSA SHA256 2020 CA1)
  - Root G2 Certificate ([DigiCert Global Root G2](#digicertglobalrootg2crtpem---tls-digicert-root-g2-certificate))
- Signed by Digicert
- This is the `connect.nulogy.net` server side certificate for our Production environment
- For use with CNEDI and B2Bi Production
- Note about the file name: .crt and .pem file extensions are used interchangebly

#### [301-connect-na-qa.nulogy.net.crt](301-connect-na-qa.nulogy.net.crt) - AS2 signing/encryption Certificate for UAT Environment

- Subject: `CN=connect-na-qa.nulogy.net,OU=Integrations,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA`
- Serial Number: 17705727081225065378 (`0xf5b760f8ae6f13a2`)
- Expires **April 2027**
- This is a x.509 V3 5 year self-signed AS2 signing/encryption certificate
- For use with CNEDI and B2Bi UAT

#### [302-connect.nulogy.net.crt](302-connect.nulogy.net.crt) - AS2 signing/encryption Certificate for Production Environment

- Subject: `CN=connect.nulogy.net,OU=Integrations,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA`
- Serial Number: 13992631575093187943 (`0xc22fd0480a581567`)
- Expires **April 2027**
- This is a x.509 V3 5 year self-signed AS2 signing/encryption certificate
- For use with CNEDI and B2Bi Production

## Scheduled Expiry Dates

Please check the expiry date on the certificate you install. The expiry dates are noted above. 

You can also use the OpenSSL utility included with most Unix-like operating systems:
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

## Copyright

The material in this repo is provided Copyright Nulogy Corporation 2022 - All Rights Reserved

Nulogy customers in good standing are licensed to use these x509 certificates only for connecting to Nulogy Corporation assets as prescribed by our standard operating procedures and by support instructions.

Digicert Root certificates are a property of Digicert.
