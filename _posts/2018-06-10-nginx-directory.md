---
layout: post
title: "How to enable directory listing in Nginx?"
subtitle: "Setting up nginx to list files and folders in a directory."
date: 2018-06-10 02:12:09 -0300
background: '/img/posts/webp/nginx.webp'
permalink: 'how-to-enable-directory-listing-in-nginx/'
---

I have just migrated my website from Apache to Nginx. The reasons for this can be another topic of a new blog post. But the main reason for me was to learn something new.

I use this website not only for blog posting but also for sharing files. Sometimes I need to make some files or folders online. On Apache, the folders which are located under `/var/www/html` can be listed with an HTTP GET request on the browser by default. But Nginx web server needs a simple configuration.

## Configuring Nginx

When the web server receives an HTTP GET request, it first looks for some index files like index.php in the requested directory. If it can’t find any index file, then It shows “HTTP 403 forbidden” error. To make the web server list the files and folders under the directory requested, we need to add `autoindex on;` in `/etc/nginx/sites-available/default` file.

To make directory listing enabled for all site, we can put it like following:

```nginx
server {
        listen 80 default_server;
        listen [::]:80 default_server;
        root /var/www/html;

        index index.php index.html index.htm;

        server_name domain.com www.domain.com;

        location / {
                autoindex on;
        }
}
```

To make only specific folders available for listing, go for it like this:

```nginx
location /testDirectory/ {
    autoindex on;
}
```

Restart Nginx to apply your changes. `service nginx restart`

## Result

When I make GET request for the directory I've configured, it lists files and folders like this:

![nginx-directory-listing](/img/posts/webp/nginx-dricetory-listing.webp){:.img-fluid}

## References

- [https://serverfault.com/questions/811409/nginx-directory-listing-on-ubuntu](https://serverfault.com/questions/811409/nginx-directory-listing-on-ubuntu)