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

## References

* https://community.letsencrypt.org/t/wildcard-with-certbot-on-aws/86461/12
* https://www.codementor.io/@slavko/wildcard-certificates-from-letsencrypt-on-aws-cloud-vfw3nftk3
* https://certbot.eff.org/docs/certbot.pdf
