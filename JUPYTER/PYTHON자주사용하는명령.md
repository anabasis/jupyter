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
