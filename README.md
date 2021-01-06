# wildcard-cert-creation

## Install certbot
<pre>
wget https://dl.eff.org/certbot-auto
chmod a+x ./certbot-auto
sudo ./certbot-auto
</pre>

## Run certbot
<pre>
certbot certonly -d staging.yourdomain.com -d *.staging.yourdomain.com --dns-route53 --logs-dir ~/letsencrypt/log/ --config-dir ~/letsencrypt/config/ --work-dir /home/username/letsencrypt/work/ -m git@voronenko.info --agree-tos --non-interactive --server https://acme-v02.api.letsencrypt.org/directory
</pre>

## Convert to pfx
<pre>
openssl pkcs12 -export -out certificate.pfx -inkey privateKey.key -in certificate.crt -certfile more.crt
</pre>

## References

* https://community.letsencrypt.org/t/wildcard-with-certbot-on-aws/86461/12
* https://www.codementor.io/@slavko/wildcard-certificates-from-letsencrypt-on-aws-cloud-vfw3nftk3
* https://stackoverflow.com/questions/808669/convert-a-cert-pem-certificate-to-a-pfx-certificate
* https://certbot.eff.org/docs/certbot.pdf
