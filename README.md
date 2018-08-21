# python-Pool
Pool多线程爬取百度度贴吧

from multiprocessing.dummy import Pool
import requests
import time

url = 'https://tieba.baidu.com/p/4543639472?pn='
link = []
def geturl(url):
    response = requests.get(url)

for i in range(1,21):
    link.append(url+str(i))
tim1 = time.time()
for l in link:
    print(l)
    geturl(l)
time2 = time.time()
print(str(time2-tim1))

pool = Pool(4)
time3 = time.time()
html = pool.map(geturl,link)
pool.close()
pool.join()
time4 = time.time() 
print('多线程耗时为%s'%(str(time4-time3)))
