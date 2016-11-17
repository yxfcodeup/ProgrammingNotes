#### python selenium使用
* 安装
```
yum install libxslt*  
yum install libxml*  
yum install xvfb
yum install -y gcc ruby-devel libxml2 libxml2-devel libxslt libxslt-devel
yum install python-lxml*
pip install lxml  
pip install -U selenium
pip install pyvirtualdisplay
```

代码：
```
from selenium import webdriver
from selenium.common.exceptions import NoSuchElementException
from selenium.webdriver.common.keys import Keys
from pyvirtualdisplay import Display

display = Display(visible=0 , size=(1024,768))
display.start()
profile = webdriver.FirefoxProfile()
profile.set_preference("network.proxy.type" , 2)
profile.set_preference("network.proxy.autoconfig_url" , "http://45.32.7.121:8388")
profile.update_preferences()
browser = webdriver.Firefox(profile)
browser.get("http://www.baidu.com")
page_html = browser.page_source
print page_html
browser.close()
display.stop()
```

#### python spynner使用
* 安装  
```
yum install xorg-x11-server-Xvfb*  
yum install PyQt4*  
yum install libX11*  
yum install xorg*
yum install libXtst-devel
yum install libpng libpng-devel
git clone https://github.com/makinacorpus/spynner.git  
cd spynner  
python setup.py install  
```

#### 使用wget爬取
```
import os
os.system('wget -r --spider http://diameizi.diandian.com 2>|log.txt')
```
Ps：上面这个网址有美女照片  
Pss:基本思想是把wget输出的标准错误流重定向到文件  
然后在读取这个log.txt文件解析吧～wget的输出很标准大家都懂的。。
随便目测了一下。。这个网站从去年九月到今天的全部美女照片都在里面了。。  
本来想用grep的。。但是定向稍微有点问题。。就没用。。  
这种方法可以防止一些反爬虫的现象。  
收集的美女中除了来自diameizi，还有来自moko.cc的。。  
不过此方法无法爬取ajax的数据。  

#### 爬虫小经验
* 对于爬取的json文件处理
To summarize the conversation in the comments:  
    * There is no need to use simplejson library, the same library is included with Python as the json module.  
    * There is no need to decode a response from UTF8 to unicode, the simplejson / json .loads() method can handle UTF8 encoded data natively.  
    * pycurl has a very archaic API. Unless you have a specific requirement for using it, there are better choices.  
requests offers the most friendly API, including JSON support. If you can, replace your call with:  
```
import requests
return requests.get(url).json()
```
* 动态网页使用selenium  
* 对于js动态获取的信息，可以使用wireshark等抓包工具去分析GET和POST信息，寻找规律，或许可以跳过从页面获取信息  
* 对于selenium中可以click的地方，使用xpath配合selenium去click，从而达到页面更改  
* 滑动页面等操作，可以使用js中的scrollTo()或其他代码实现  
* 爬虫可用工具有：xpath、正则表达式、BeautifuSoup、selenium、JavaScript、wireshark、pyvirtualdisplay
* js代码示例
使用selenium本身点击：
```
WebElement opt=driver.findElement(By.id(“optionsLink”));  
opt.click();  
```
selenium2使用JS点击页面元素的方法：
```
JavascriptExecutor js = (JavascriptExecutor) driver;
js.executeScript(“arguments[0].click();”,driver.findElement(By.id(“optionsLink”)));
```

#### 常见问题  
1. Selenium using Python - Geckodriver executable needs to be in PATH  
```
selenium.common.exceptions.WebDriverException: Message: 'geckodriver' executable needs to be in PATH.
```  
[First of all you will need to download latest executable geckodriver from here to run latest firefox using selenium](https://github.com/mozilla/geckodriver/releases)  
Actually The Selenium client bindings tries to locate the geckodriver executable from the system PATH. You will need to add the directory containing the executable to the system path.  
* On Unix systems you can do the following to append it to your system’s search path, if you’re using a bash-compatible shell:  
```
export PATH=$PATH:/path/to/directory/of/executable/downloaded/in/previous/step
```  

* On Windows you will need to update the Path system variable to add the full directory path to the executable geckodriver [manually](https://www.google.co.in/amp/www.howtogeek.com/118594/how-to-edit-your-system-path-for-easy-command-line-access/amp/?client=ms-android-motorola) or [command line](https://www.windows-commandline.com/set-path-command-line/) (don't forget to restart your system after adding executable geckodriver into system PATH to take effect). The principle is the same as on Unix.  

Now you can run your code same as you're doing as below :  
```
from selenium import webdriver  
browser = webdriver.Firefox() 
```  

```
selenium.common.exceptions.WebDriverException: Message: Expected browser binary location, but unable to find binary in default location, no 'moz:firefoxOptions.binary' capability provided, and no binary flag set on the command line  
```

Exception clearly states you have installed firefox some other location while Selenium is trying to find firefox and launch from default location but it couldn't find. You need to provide explicitly firefox installed binary location to launch firefox as below :  
```
from selenium import webdriver
from selenium.webdriver.firefox.firefox_binary import FirefoxBinary
binary = FirefoxBinary('path/to/installed firefox binary')
browser = webdriver.Firefox(firefox_binary=binary)
```


#### 参考链接
* [抓取淘宝 MM 照片](http://wiki.jikexueyuan.com/project/python-crawler-guide/mm.html)
* [当python爬虫遇到10060错误](http://dataunion.org/23934.html)
* [用Python写一个简单的微博爬虫](http://dataunion.org/23004.html)
* [Python爬虫利器二之Beautiful Soup的用法](http://cuiqingcai.com/1319.html)
* [Web爬虫：多线程、异步与动态代理初步](http://www.freebuf.com/articles/web/104732.html)
* [Selenium Documents](https://pypi.python.org/pypi/selenium)
* [Beautiful Soup 4.2.0 Documents](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/#id25)
* [Scrapy Documents](http://scrapy-chs.readthedocs.io/zh_CN/0.24/intro/tutorial.html)
* [如何用Python抓取动态页面信息](http://www.open-open.com/lib/view/open1413965931622.html)
* [淘宝爬虫](http://blog.chinaunix.net/uid-23500957-id-3858913.html)
* [Python爬虫实战之：模拟登录淘宝并获取所有订单](http://dataunion.org/22388.html)
* [Scrapy爬虫抓取动态网站](http://chenqx.github.io/2014/12/23/Spider-Advanced-for-Dynamic-Website-Crawling/)
* [Scrapy爬虫抓取网站数据](http://chenqx.github.io/2014/11/09/Scrapy-Tutorial-for-BBSSpider/)
* [Web爬虫：多线程、异步与动态代理初步](http://www.freebuf.com/articles/web/104732.html)
* [模拟登陆一些知名的网站](https://github.com/xchaoinfo/fuck-login)
* [怎样用Python设计一个爬虫模拟登陆知乎？](https://www.zhihu.com/question/29925879)
* [简易爬虫](http://mp.weixin.qq.com/s?__biz=MzA3OTUxNDY2MA==&mid=2247483758&idx=1&sn=394a28df511ac0505291b0c519c43865&scene=1&srcid=0714qyKZ7YU1g5yOZBSwaU5K&from=groupmessage&isappinstalled=0#wechat_redirect)  
* [Python即时网络爬虫项目: 内容提取器的定义](https://segmentfault.com/a/1190000005344687)  
* [python爬虫：dht磁力源代码开源](https://segmentfault.com/a/1190000006671235)  
* [python爬虫爬取百度网盘-怎么做一个百度网盘搜索引擎](https://segmentfault.com/a/1190000005105528)  
* [Selenium using Python - Geckodriver executable needs to be in PATH](http://stackoverflow.com/questions/40208051/selenium-using-python-geckodriver-executable-needs-to-be-in-path)