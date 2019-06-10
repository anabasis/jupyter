# PYTHON 자주사용하는 구문

## 웹서버 정보

```python
!pip install builtwith

from builtwith import builtwith
builtwith("http://www.wrodpress.com")

{'web-servers': ['Nginx'],
 'font-scripts': ['Google Font API'],
 'ecommerce': ['WooCommerce'],
 'cms': ['WordPress'],
 'programming-languages': ['PHP'],
 'blogs': ['PHP', 'WordPress']}
```

## WHOIS

```python
!pip install python-whois

from whois import whois
whois("http://www.google.com")
```

## Robot정보

```python
from urllib import robotparser

robot = robotparser.RobotFileParser()
robot.set_url('http://www.google.com.com/robots.txt')
```

## Request

```python
from urllib import request, parse, error
try :

    # URLOPEN
    resp = request.urlopen("http://www.google.com")

    # URLREQUEST
    #url = "https://www.google.com/search?q=%EB%B0%95%EB%B3%B4%EC%98%81&rlz=1C1CHBD_koKR847KR847&oq=%EB%B0%95%EB%B3%B4%EC%98%81&aqs=chrome..69i57j0l5.3532j0j8&sourceid=chrome&ie=UTF-8"
    #req = request.Request(url,headers={"User-Agent":"Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; rv:11.0) like Gecko"},method="GET")

except error.HTTPError as e :
    resp.geturl()
    resp.reason
    resp.getcode()
    print(resp.info())
    resp.getheaders()
```

## URL

- URL Parsing

```python
from urllib import parse

result = parse.urlparse("https://www.google.com/search?q=%EB%B0%95%EB%B3%B4%EC%98%81")
[_ for _ in result]
['https', 'www.google.com', '/search', '', 'q=%EB%B0%95%EB%B3%B4%EC%98%81', '']

parse.urljoin("https://www.google.com/search?q=%EB%B0%95%EB%B3%B4%EC%98%81","/search/about")
'https://www.google.com/search/about'
```

## request

```python
import requests
header = {"User-Agent": 'Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; rv:11.0) like Gecko'}
resp = requests.get("http://www.google.com/search", params={"q":"박보영"}, headers=header)

resp.status_code, resp.reason, resp.headers, resp.text
resp.content ## content가 Bite
resp.encoding = "utf-8"
```

## requests

```python
import requests
resp = requests.request("get","http://httpbin.org/get", params={"key":"value"})
```

```python
import requests
# 200 => OK
# 400 => My Fault
# 500 => You Fault => Traffic 과도하게 증가
header={"User-Agent":"Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; rv:11.0) like Gecko"}

def download(url, params ={}, retries = 3) :
    resp = None
    try :
        resp = requests.get(url, params = params, headers = header)
        resp.raise_for_status()
        #html = requests.post(url, params)

    except requests.exceptions.HTTPError as e :
        if 500 <= e.response.status_code < 600 and retries > 0:
            print(retries)
            resp = download(url, params, retries - 1)
        else :
            print(e.response.status_code)
            print(e.response.reason)
            print(e.response.headers)
    return resp
```

## JSON

```python
import json

result = json.loads(resp.content)
result["args"]["key"]
```

## Cookie

```python
html.cookies.get_dict()

html = requests.get(url,cookies=html.cookies)
html.text
```

## BeautifulSoup

```python
from bs4 import BeautifulSoup
dom = BeautifulSoup(html,"lxml")

try :
    dom.span.attr
except AttributeError as e :
    print("Not Found")

dom.html.body.p, dom.p, [_ for _ in dom.p.children]
dom.prettify()
```

<table>
<tr><td>find</td><td>(name,attrs,recursive,string,**kwargs)</td><td></td></tr>
<tr><td>find_all</td><td>(name,attrs,recursive,string,**kwargs)</td><td></td></tr>
<tr><td>find_parent</td><td></td><td></td></tr>
<tr><td>find_parents</td><td></td><td></td></tr>
<tr><td>find_all</td><td></td><td></td></tr>
<tr><td>find_all(recursive=false)</td><td>-</td><td></td></tr>
<tr><td>find_next_sibling<br/>find_previous_siling</td><td>-</td><td></td></tr>
<tr><td>find_next_siblings<br/>find_previous_siblings</td><td>-</td><td></td></tr>
</table>

## Selenium

```python
!pip install selenium

from selenium import webdriver
```

find_element_by_id
find_element_by_name
find_element_by_xpath
find_element_by_link_text
find_element_by_partial_link_text
find_element_by_tag_name
find_element_by_class_name
find_element_by_css_selector

find_elements_by_name
find_elements_by_xpath
find_elements_by_link_text
find_elements_by_partial_link_text
find_elements_by_tag_name
find_elements_by_class_name
find_elements_by_css_selector

## defaultdict

<https://bslife.tistory.com/37>
<https://codeday.me/ko/qa/20190317/86894.html>
<https://dojang.io/mod/page/view.php?id=2307>
