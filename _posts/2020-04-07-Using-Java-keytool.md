---
tags: [Java, Secure Chat Server 1, OpenSSL]
date: 2020-04-07
---
Before embarking on rewriting my Secure Chat Server 1 from Java into C#, I spent some time reviewing Oracle's documentation for Java CAPS. These guides were invaluable for me when [I made a 100% Java written client and server][secChat1] which needed to access certificates and exchange them to create an SSL connection, as well as for other cryptography protocols I implemented.

I will provide them below for future reference:

### My favorite tutorials for Java keytool and signing certificates with OpenSSL

- [Java Keytool docs](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/keytool.html)

- What is a keystore?

  [A KeyStore consists of a database containing a private key and an associated certificate](https://docs.oracle.com/cd/E19509-01/820-3503/ggffo/index.html)

- explanation on how to use OpenSSL to sign a certificate held in a Java keystore:

  [Using the OpenSSL Utility for the LDAP and HTTPS Adapters \(Configuring Java CAPS for SSL Support\)
  Creating a KeyStore in JKS Format](https://docs.oracle.com/cd/E19509-01/820-3503/ggfen/index.html)

- JDK Security API

  [Generating a Certificate Signing Request (CSR) for a Public Key Certificate](https://docs.oracle.com/javase/tutorial/security/sigcert/index.html#GenCSR)

[secChat1]: {{ site.github_url | append: site.data.github["Secure Chat Server 1"].url }}
