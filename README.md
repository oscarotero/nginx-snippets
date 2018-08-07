# nginx-snippets

Custom snippets for nginx with http2

## Install

```
cd /etc/nginx/snipptes
git clone https://github.com/oscarotero/nginx-snippets.git
```

```conf
server {
  listen 443 ssl http2;
  listen [::]:443 ssl http2;

  include snippets/nginx-snippets/global.conf;

  location / {
    include snippets/nginx-snippets/html-headers.conf;
  }

  # Media: images, icons, video, audio, HTC
  location ~* \.(?:jpg|jpeg|gif|png|ico|cur|gz|svg|mp4|ogg|ogv|webm|htc)$ {
    include snippets/nginx-snippets/media-headers.conf;
  }

  # Fonts
  location ~* \.(?:ttf|ttc|otf|eot|woff|woff2)$ {
    include snippets/nginx-snippets/fonts-headers.conf;
  }

  # CSS
  location ~* \.css$ {
    include snippets/nginx-snippets/css-headers.conf;
  }

  # Javascript
  location ~* \.js$ {
    include snippets/nginx-snippets/js-headers.conf;
  }
}
```

## Other tools

- Configure CSP: [CSP is Awesome](https://www.cspisawesome.com/):
- Configure SSL: [Mozilla SSL Configuration Generator](https://mozilla.github.io/server-side-tls/ssl-config-generator/)

## Testing

- [Observatory by Mozilla](https://observatory.mozilla.org/)
- [Sonarwhal](https://sonarwhal.com/)