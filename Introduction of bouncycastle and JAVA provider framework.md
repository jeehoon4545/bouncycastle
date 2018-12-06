#### Introduction to BouncyCastle with Java

=====================================================
## 1. Overview
BouncyCastle is a Java library that complements the default Java Cryptographic Extension (JCE).
In this introductory article, we’re going to show how to use BouncyCastle to perform cryptographic operations, such as encryption and signature.

## 2. Maven Configuration
Before we start working with the library, we need to add the required dependencies to our pom.xml file:

## 3. Setup Unlimited Strength Jurisdiction Policy Files
The standard Java installation is limited in terms of strength for cryptographic functions, this is due to policies prohibiting the use of a key with a size that exceeds certain values e.g. 128 for AES.
To overcome this limitation, we need to configure the unlimited strength jurisdiction policy files.
Finally, we need to look for the {JAVA_HOME}/lib/security folder and replace the existing policy files with the ones that we’ve extracted here.
Note that in Java 9, we no longer need to download the policy files package, setting the crypto.policy property to unlimited is enough:
Based on the maximum key size returned by the getMaxAllowedKeyLength() method, we can safely say that the unlimited strength policy files have been installed correctly.
If the returned value is equal to 128, we need to make sure that we’ve installed the files into the JVM where we’re running the code.

## 4. Cryptographic Operations

## 4.1. Preparing Certificate And Private Key
Before we jump into the implementation of cryptographic functions, we first need to create a certificate and a private key.

## 4.2 CMS/PKCS7 Encryption And Decryption
In asymmetric encryption cryptography, each communication requires a public certificate and a private key.

## 4.3 CMS/PKCS7 Signature And Verification
Signature and verification are cryptographic operations that validate the authenticity of data.

## 5. Conclusion
In this article, we’ve discovered how to use the BouncyCastle library to perform basic cryptographic operations, such as encryption and signature.
In a real-world situation, we often want to sign then encrypt our data, that way, only the recipient is able to decrypt it using the private key, and check its authenticity based on the digital signature.
The code snippets can be found, as always, over on GitHub.
