# wildcard-cert-creation

## Docker command
<pre>
docker run -it --rm --name certbot \
    --env AWS_ACCESS_KEY_ID=<PUT_YOUR_OWN_ID> \
    --env AWS_SECRET_ACCESS_KEY=<PUT_YOUR_OWN_KEY> \
    --env AWS_SESSION_TOKEN=<PUT_YOUR_OWN_TOKEN> \
    -v "<PUT_YOUR_LOCAL_DIR>/letsencrypt:/etc/letsencrypt" \
    -v "<PUT_YOUR_LOCAL_DIR>/letsencrypt:/var/lib/letsencrypt" \
    certbot/dns-route53 certonly \
    -d my-subdomain.example.com \
    -d '*.sys.my-subdomain.example.com' \
    -d '*.login.sys.my-subdomain.example.com' \
    -d '*.uaa.sys.my-subdomain.example.com' \
    -d '*.apps.my-subdomain.example.com' \
    -m <PUT_YOUR_EMAIL> \
    --agree-tos --server https://acme-v02.api.letsencrypt.org/directory
</pre>

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

## Validate a CSR

## References

* https://community.letsencrypt.org/t/wildcard-with-certbot-on-aws/86461/12
* https://www.codementor.io/@slavko/wildcard-certificates-from-letsencrypt-on-aws-cloud-vfw3nftk3
* https://stackoverflow.com/questions/808669/convert-a-cert-pem-certificate-to-a-pfx-certificate
* https://community.letsencrypt.org/t/manual-cert-with-custom-csr-to-be-renewed-with-dns-route53/57436
* https://www.digitalocean.com/community/tutorials/how-to-use-certbot-standalone-mode-to-retrieve-let-s-encrypt-ssl-certificates-on-ubuntu-16-04
* https://certbot.eff.org/docs/certbot.pdf
