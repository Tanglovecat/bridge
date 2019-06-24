# bridge
Python 异步编程之asyncio

- Python 由于GIL全局锁的存在， 不能发挥多核优势。  
- 但在IO 密集型的网络编程中， 异步处理比同步处理能提升成百上千的效率， 弥补了python 性能方面的短板

## 同步/异步
- 同步 是指完成事务的逻辑， 先执行第一个事务， 如果阻塞了， 会一直等待， 直到这个事务完成， 再执行第二个事务， 顺序执行； 
- 异步 是和同步相对的， 异步是指在处理调用这个事务之后， 不会等待这个事务的处理结果， 直接处理第二个事务去了， 通过状态、通知、回调来通知调用者处理结果。

## 一、asyncio
## 二、aiohttp
![baidu](http://www.baidu.com/img/bdlogo.gif "百度logo") 
```
from aiohttp import ClientSession
async with ClientSession() as session:
  async with session.get(url) as response:
```

aiohttp 异步实现的例子:
```
import asyncio
from aiohttp import ClientSession

tasks = []
url = "https://www.baidu.com/{}"
async def hello(url):
  async with ClientSession() as session:
    async with session.get(url) as response:
      respomse = wait response.read()
      print(response)
      
if __name__ == '__main__':
  loop = asyncio.get_event_loop()
  loop.run_until_complete(hello(url))
```

