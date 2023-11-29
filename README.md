# Extension
Extension in profile

## Mitm
```
extension:
  - name: "redirect"
    type: mitm
    action: redirect
    hosts:
      - +.google.cn
      - +.google.com
    match:
      - ^http?://www\.google\.cn https://www.google.com 307
      - ^http?://www\.google\.cn(.*) https://www.google.com$1 302
      
  - name: "reject"
    type: mitm
    action: reject
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http request header"
    type: mitm
    action: modify-request-header
    modify:
      - baidu Paidu
      - (\n)Cookie:.+(\n) Cookie: newCookie
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http request boby"
    type: mitm
    action: modify-request-boby
    modify:
      - old new
      - (\n)key:.+(\n) key: new
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http response header"
    type: mitm
    action: modify-response-header
    modify:
      - baidu Paidu
      - (\n)key:.+(\n) key: newCookie
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http response boby"
    type: mitm
    action: modify-response-boby
    modify:
      - baidu Paidu
      - (\n)key:.+(\n) key: new
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com
```
## TODO
- [ ] modify http request and response with javascript
