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
      - (\r\n)Cookie:.+(\r\n) $1Cookie: newCookie$2
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http request boby"
    type: mitm
    action: modify-request-boby
    modify:
      - old new
      - (\r\n)key:.+(\r\n) $1key: new$2
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http response header"
    type: mitm
    action: modify-response-header
    modify:
      - baidu Paidu
      - (\r\n)key:.+(\r\n) $1key: newCookie$2
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http response boby"
    type: mitm
    action: modify-response-boby
    modify:
      - baidu Paidu
      - (\r\n)key:.+(\r\n) $1key: new$2
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com
```
## TODO
- [ ] modify http request and response with javascript
