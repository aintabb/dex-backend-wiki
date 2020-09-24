In some cases when developing on Linux you will experience issues where the API is unable to validate the certificate of the Identity Server. This error will show after authenticating and trying to make a call to an authorized endpoint. You will see an error that will say something regarding the https//localhost:5005/.well-known/openid-configuration url.

**How to fix this?**
* `dotnet dev-certs https --clean` to clean any old certificates
* `dotnet dev-certs https -v` to generate a self-signed cert
* `cd ~/.dotnet/corefx/cryptography/x509stores/my`
* `ls -all` and check for a cerficate with the .pfx extension.
* Convert the existing certificate from pfx to pem using `openssl pkcs12 -in <certname>.pfx -nokeys -out localhost.crt -nodes`
* `cp localhost.crt /usr/local/share/ca-certificates` copy localhost.crt to /usr/local/share/ca-certificates
* Trust the certificate using `sudo update-ca-certificates`
* Verify that the verification failed using `openssl verify localhost.crt`  
Output should be similar to  
```
$ openssl verify localhost.crt
CN = localhost
error 20 at 0 depth lookup: unable to get local issuer certificate
error localhost.crt: verification failed
```

* Manually generate a self-signed certificate (without using dotnet). `touch localhost.conf`
* `nano localhost.conf` to start editing the new file
* Copy the following contents and paste it in the file:
```
[req]
default_bits       = 2048
default_keyfile    = localhost.key
distinguished_name = req_distinguished_name
req_extensions     = req_ext
x509_extensions    = v3_ca

[req_distinguished_name]
commonName                  = Common Name (e.g. server FQDN or YOUR name)
commonName_default          = localhost
commonName_max              = 64

[req_ext]
subjectAltName = @alt_names

[v3_ca]
subjectAltName = @alt_names
basicConstraints = critical, CA:false
keyUsage = keyCertSign, cRLSign, digitalSignature,keyEncipherment

[alt_names]
DNS.1   = localhost
DNS.2   = 127.0.0.1
```
* Generate the certificate using `openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout localhost.key -out localhost.crt -config localhost.conf`
* Convert .crt to .pfx using `openssl pkcs12 -export -out localhost.pfx -inkey localhost.key -in localhost.crt`
* Verify certificate by using `openssl verify -CAfile localhost.crt localhost.crt` The value should be something along the line: `localhost.crt: OK`
* Copy the .crt file to /usr/local/share/ca-certificates using `cp localhost.crt /usr/local/share/ca-certificates`
* Trust the certificate using `sudo update-ca-certificates`
* Update permissions of the .pfx file using: `sudo chmod 777 /usr/local/share/ca-certificates/localhost.pfx`
* Copy the .pfx file in /usr/local/share/ca-certificates to ~/.dotnet/corefx/cryptography/x509stores/my using: `cp localhost.pfx ~/.dotnet/corefx/cryptography/x509stores/my`
* We're nearly ready. We just have to add some small code changes in both our API/appsettings.development.json and IdentityServer/appsettings.development.json
Add the following code at the end of the file:
```
"Kestrel": {
  "Certificates": {
    "Default": {
      "Path": "/usr/local/share/ca-certificates/localhost.pfx",
      "Password": ""
    }
  }
}
```
You should now be able to start the API and Identity Server without issues.   
Massive credits to [this stackoverflow post](https://stackoverflow.com/questions/55485511/how-to-run-dotnet-dev-certs-https-trust/59702094#59702094) that helped me out a lot to fix this issue.