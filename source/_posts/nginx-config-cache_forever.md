---
title: Nginx config for caching files forever
date: 2020-12-27 19:00:00
updated: 2020-12-27 19:00:00
categories:
- Nginx
tags:
- Nginx
- Web Server
---

Use following config, nginx server don't cache files with html extension and all files in the dynamic_1 and dynamic_2 folders, but it cache other files for one year at /srv/www.

```txt
server {
    listen 8001;
    root /srv/www;

    location ~* \.html$ {
      # Inherit default of parent, that is not cache control.
      # For the html file.
    }

    location ~* \.*$ {
      location ~ /(dynamic_1|dynamic_2) {
        # Close expires for cache control, that is recover to default
        # For the dynamic_1 and dynamic_2 subdirectories.
        expires off;
      }
      # Cache one year
      # For other files.
      expires 1y;
    }
}
```
