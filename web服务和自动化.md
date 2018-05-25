# Web服务和自动化
## webbrowser模块
调用标准库webbrowser模块并让浏览器显示一个Python入门网页：

    import webbrowser
    url = 'http://www.python.org/'
    webbrowser.open(url)
在新的标签中打开它：

    import webbrowser
    url = 'http://www.python.org/'
    webbrowser.open_new_tab(url)
webbrowser可以完全控制浏览器

## Web API和表述性状态传递
可以通过API来提供数据，数据不是HTML网页，而是更容易被程序处理的格式，比如JSON和XML

表述性状态传递（REST），一个web接口。
## JSON
pass
# 抓取数据
scrapy框架。
## 用BeautifulSoup来抓取数据，
尝试用BeautifulSoup获取一个网页上的所有链接。HTML的a元素表示一个链接，href属性表示链接的目标地址：

    def get_links(url):
    import requests
    from bs4 import BeautifulSoup as soup
    result = requests.get(url)
    page = result.text
    doc = soup(page)
    links = [element.get('href') for element in doc.find_all('a')]


if __name__ == '__main__':
    import sys
    for url in sys.argv[1:]:
        print('links in', url)
        for num, link in enumerate(get_links(url), start=1):
            print(num, link)
        print()