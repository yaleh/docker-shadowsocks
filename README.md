docker-shadowsocks
==================

This Dockerfile builds an image with the Python implementation of [shadowsocks](https://github.com/clowwindy/shadowsocks), pen(for balancing), nginx(for a web server of PAC file), and even a cron job to measure the health of Shadowsocks connections and update pen states according to it. Based on Ubuntu 14.04 image.

Quick Start
-----------

It's required to build customize supervisord.conf and mount the folder of the supoervisord.conf file as a volume. 

    docker run -p 1990:1990 -p 2222:22 -p 1989:1989 -p 8000:80 --name ss -v $PWD:/usr/share/nginx/html -v $PWD:/etc/supervisor/conf.d -d -i yaleh/docker-shadowsocks

Ports to map

* 22: SSH
* 1989: balanced SOCK5 proxy
* 1990: Pen control

Volumes to mount

* /usr/share/nginx/html: folder to save pen status HTML
* /etc/supervisor/conf.d: folder for supervisord.conf

For more command line options, refer to the [shadowsocks documentation](https://github.com/clowwindy/shadowsocks)
