# nginx-snippets

Custom snippets for nginx with http2

## Install

```
cd /etc/nginx/snippets
git clone https://github.com/oscarotero/nginx-snippets.git
```

## Snippets

This package contains a set of config files with best practices that you can include in your nginx config.

- `http.conf`: Common http settings to include inside the `http` block.
- `server.conf`: Common http settings to include inside each `server` block.
- `html.conf`: Settings, headers and security stuff to use with html responses.
- `media.conf`:  Settings, headers and security stuff to use with media responses (images, videos, audio, etc).
- `css.conf`:  Settings, headers and security stuff to use with css responses.
- `js.conf`:  Settings, headers and security stuff to use with javascript responses.
- `fonts.conf`:  Settings, headers and security stuff to use with fonts responses (otf, woff, woff2, etc).

## Usage

```conf
http {
  include snippets/nginx-snippets/http.conf;
  
  server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;

    include snippets/nginx-snippets/server.conf;

    location / {
      include snippets/nginx-snippets/html.conf;
    }

    # Media: images, icons, video, audio, HTC
    location ~* \.(?:jpg|jpeg|gif|png|ico|cur|gz|svg|mp4|ogg|ogv|webm|htc)$ {
      include snippets/nginx-snippets/media.conf;
    }

    # Fonts
    location ~* \.(?:ttf|ttc|otf|eot|woff|woff2)$ {
      include snippets/nginx-snippets/fonts.conf;
    }

    # CSS
    location ~* \.css$ {
      include snippets/nginx-snippets/css.conf;
    }

    # Javascript
    location ~* \.(?:js|webmanifest)$ {
      include snippets/nginx-snippets/js.conf;
    }
  }
}
```

## Other tools

- Configure CSP: [CSP is Awesome](https://www.cspisawesome.com/):
- Configure SSL: [Mozilla SSL Configuration Generator](https://mozilla.github.io/server-side-tls/ssl-config-generator/)
- NGINX Config Generator: [nginxconfig.io](https://nginxconfig.io/)

## Testing

- [Observatory by Mozilla](https://observatory.mozilla.org/)
- [Webhint](https://webhint.io/scanner/)
- [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
