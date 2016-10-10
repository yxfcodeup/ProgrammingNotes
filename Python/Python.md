## Python
### 使用requests库抓取页面的时候的编码问题  
首先，sys.setdefaultencoding is evil。  
1. 如果 Requests 检测不到正确的编码，那么就告诉它正确的是什么：  
```
response.encoding = 'gbk'  
print(response.text)
```

2. 原始内容在response.content里，bytes
3. 单个请求完全没必要用session，直接reqeusts.get(xxx)就可以了

以下是python3，python2在那个字符串前加u告诉它是Unicode也一样。
```
>>> '°æÈ¨ËùÓÐ 2013 ¶«ÄÏ´óÑ§ÍøÂçÓëÐÅÏ¢ÖÐÐÄ'.encode('latin1').decode('gbk')
'版权所有 2013 东南大学网络与信息中心'
```

### python两种生成md5的方法
1. 使用md5包  
```
import md5
src = 'this is a md5 test.'   
m1 = md5.new()   
m1.update(src)   
print m1.hexdigest()   
```

2. 使用hashlib
```
import hashlib   
m2 = hashlib.md5()   
m2.update(src)   
print m2.hexdigest()   
```

### 查看进程是否存在
```
import os
os.path.exists("/proc/0")
os.path.exists("/proc/12")
```

### 实现zip文件暴力破解  
```
import zipfile 
try:
    with zipfile.ZipFile('1.zip') as zFile:     #创建ZipFile对象
        #解压文件
        zFile.extractall(path='./',pwd=b'1314')
        print('Extract the Zip file successfully!')
except:
    print('Extract the Zip file failed!')

```



### Python第三方库下载地址
1. [http://www.lfd.uci.edu/~gohlke/pythonlibs/](http://www.lfd.uci.edu/~gohlke/pythonlibs/)

### 参考链接
1. [https://segmentfault.com/a/1190000006872491](https://segmentfault.com/a/1190000006872491)