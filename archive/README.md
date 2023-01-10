## Archive

We prefer to maintain the old expired certs for posterity. Therefore, the archive folder will hold all the old and expired
certificates that are no longer in rotation, as well as descriptions about their past uses.

## Contents

The files contained in this repository are as follows.


#### 002-axway-test.nulogy.net-i4-sha1.crt / 003-axway-test.nulogy.net-i4-sha256.crt - B2Bi Test Certificate, with SHA-1 or SHA-256 Signatures by I4

- `C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Integrations, CN=axway-test.nulogy.net`
- Expired January 2021

- These are our axway-test.nulogy.net server side certificates for the test environment.
- This certificate has SubjectAlternativeNames (SANs) to ease future migrations.
- We may be forced to revoke and re-issue these certificates in future due to configuration changes or security requirements.


#### 004-axway.nulogy.net-i4-sha1.crt / 005-axway.nulogy.net-i4-sha256.crt - B2Bi Production Certificate, with SHA-1 or SHA-256 Signatures by I4

- `C=CA, ST=Ontario, L=Toronto, O=Nulogy Corporation, OU=Integrations, CN=axway.nulogy.net`
- Expired January 2021

- These are our axway.nulogy.net server side certificates for the production environment.
- This certificate has SubjectAlternativeNames (SANs) to ease future migrations.
- We may be forced to revoke and re-issue these certificates in future due to configuration changes or security requirements.

#### 101-axway.nulogy.net-geotrust-sha256.crt - B2Bi Production Environment Certificate, with SHA-256 Signatures by Geotrust

- `ST=Ontario, C=CA, ST=Ontario, L=Toronto/businessCategory=Private Organization/serialNumber=2018280, O=Nulogy Corporation, OU=Infrastructure, CN=axway.nulogy.net`
- Expired August 2018

- This certificate is signed by Geotrust EV, to comply with some customer's requests that our SSL certificates be validated against our legal name.

#### 102-cpi-https.nulogy.net-geotrust-sha256.crt - Shim interchange certificate, with SHA-256 Signatures by Geotrust

- `CN=RapidSSL SHA256 CA,O=GeoTrust Inc.,C=US`
- Expired December 2019

- Signed by Geotrust/RapidSSL, for data interchange.

#### 201-connect.nulogy.net.crt - Signed by Godaddy

- Expired May 10 2018
- Extended Validation
- For use with b2bi 2.3

#### 202-connect-na-qa.nulogy.net.crt - Signed by Godaddy

- Expired May 10 2018
- Extended Validation
- For use with b2bi 2.3

#### 203-wildcard.nulogy.net.crt - Signed by RapidSSL/Digicert

- Expired January 23rd 2021
- For use with B2Bi 2.3


#### 204-connect.nulogy.net-i4-sha256.crt - Production SHA-256 Signatures by I4

- `CN=connect.nulogy.net,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA, CN=Nulogy Internal Issuing CA I4,OU=Infrastructure,O=Nulogy Corporation,C=CA` 
- Expires April 27th 2022

- This is our AS2 signing/encryption certificate.
- Used for inbound on CNEDI production and outbound on B2Bi Production
- We may be forced to revoke and re-issue these certificates in future due to configuration changes or security requirements.

#### 205-connect-na-qa.nulogy.net-i4-sha256.crt - Test SHA-256 Signatures by I4

- `CN=connect-na-qa.nulogy.net,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA,CN=Nulogy Internal Issuing CA I4,OU=Infrastructure,O=Nulogy Corporation,C=CA`
- Expired April 27th 2022

- These are our *connect-na-qa.nulogy.net* server side certificates for the QA/UAT environment.
- Used for inbound and outbound on B2Bi UAT
- We may be forced to revoke and re-issue these certificates in future due to configuration changes or security requirements.

#### 206-connect.nulogy.net.crt - Signed by Digicert 

- `CN=connect.nulogy.net,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA CN=DigiCert TLS RSA SHA256 2020 CA1,O=DigiCert Inc,C=US`
- Expired November 2nd 2021

- For use with CNEDI and B2Bi
- Contains the Digicert Global Root cert as well
- These are our *connect.nulogy.net* server side certificates for the Production environment.

#### 207-connect.nulogy.net.crt - TLS Certificate Production

- `CN=connect.nulogy.net,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA, CN=DigiCert TLS RSA SHA256 2020 CA1,O=DigiCert Inc,C=US`
- Expired September 21st 2022
- Contents include:
    - Certificate (connect.nulogy.net)
    - Intermediate Certificate (DigiCert TLS RSA SHA256 2020 CA1): Expiration April 2031
    - Root Certificate (DigiCert Global Root CA): Expiration November 2031
- Signed by Digicert
- These are our *connect.nulogy.net* server side certificates for the Production environment.
- For use with CNEDI and B2Bi Production

#### 208-connect-na-qa.nulogy.net.crt - TLS Certificate UAT

- `CN=connect-na-qa.nulogy.net,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA, CN=DigiCert TLS RSA SHA256 2020 CA1,O=DigiCert Inc,C=US`
- Expired February 5th 2023
- Contents include:
  - Certificate (connect-na-qa.nulogy.net)
  - Intermediate Certificate (DigiCert TLS RSA SHA256 2020 CA1): Expiration April 2031
  - Root Certificate (DigiCert Global Root CA): Expiration November 2031
- Signed by Digicert
- These are our *connect-na-qa.nulogy.net* server side certificates for the UAT environment.
- For use with CNEDI and B2Bi UAT

#### 209-connect.nulogy.net.crt - AS2 signing/encryption Production

- This cert is active, but should not be used as it is not x.509 V3.
- `CN=connect.nulogy.net,OU=Integrations,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA`
- Expires March 2032

- This was temporarily our AS2 signing/encryption certificate.
- For use with CNEDI and B2Bi Production

#### 210-connect-na-qa.nulogy.net.crt - AS2 signing/encryption UAT

- This cert is active, but should not be used as it is not x.509 V3.
- `CN=connect-na-qa.nulogy.net,OU=Integrations,O=Nulogy Corporation,L=Toronto,ST=Ontario,C=CA`
- Expires March 2032

- This was temporarily our AS2 signing/encryption certificate.
- For use with CNEDI and B2Bi UAT

### Copyright

The material in this repo is provided Copyright Nulogy Corporation 2022 - All Rights Reserved

Nulogy customers in good standing are licensed to use these x509 certificates only for connecting to Nulogy Corporation assets as prescribed by our standard operating procedures and by support instructions.
