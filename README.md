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
    action: modify-req-header
    modify:
      - replace: baidu
        with: Paidu
      - replace:(\n)Cookie:.+(\n)
        with: Cookie: newCookie
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http request boby"
    type: mitm
    action: modify-req-boby
    modify:
      - replace: old
        with: new
      - replace: (\n)key:.+(\n)
        with: "key: new"
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http response header"
    type: mitm
    action: modify-resp-header
    modify:
      - replace: baidu
        with: Paidu
      - replace: (\n)key:.+(\n)
        with: "key: newCookie"
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http response boby"
    type: mitm
    action: modify-resp-boby
    modify:
      - replace: baidu
        with: Paidu
      - replace: (\n)key:.+(\n)
        with: "key: new"
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com
      
  - name: "modify http request with javascript"
    type: mitm
    action: modify-req-js
    path: "javascript code path"
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com

  - name: "modify http response body with javascript"
    type: mitm
    action: modify-resp-body-js
    path: "javascript code path"
    hosts:
      - +.baidu.com
    match:
      - ^http?://www\.baidu\.com
```
## TODO
- [ ] modify http request and response with javascript
