---
layout: post
title: Two examples of multi-threads in Python
date: 2016-05-22
categories: how-to
tags: [Python, Parallel Computing, Efficiency]
---

{% highlight python %}
import time
import threading
import queue
{% endhighlight%}


{% highlight python %}
class Consumer(threading.Thread):

    def __init__(self, queue):
        threading.Thread.__init__(self)
        self._queue = queue

    def run(self):
        while True:
            msg = self._queue.get()

            if isinstance(msg, str) and msg == 'quit':
                break

            print('I am a thread, and I received %s!!' %msg)

        print('Bye guys!')
{% endhighlight%}


{% highlight python %}
def Producer():
    Queue = queue.Queue()

    worker = Consumer(Queue)

    worker.start()

    start_time = time.time()

    while time.time() - start_time < 5:
        Queue.put('Something at %s' %time.time())

        time.sleep(1)

    Queue.put('quit')

    worker.join()

{% endhighlight%}


{% highlight python %}
if __name__ == '__main__':
    Producer()
{% endhighlight%}

    I am a thread, and I received Something at 1463965241.8577423!!
    I am a thread, and I received Something at 1463965242.8580678!!
    I am a thread, and I received Something at 1463965243.8581245!!
    I am a thread, and I received Something at 1463965244.858176!!
    I am a thread, and I received Something at 1463965245.85845!!
    Bye guys!


### Another instance for multi-threads


{% highlight python %}
from multiprocessing import Pool
from multiprocessing.dummy import Pool as ThreadPool
import urllib.request as request
{% endhighlight%}


{% highlight python %}
urls = [ 'http://www.python.org',
        'http://www.python.org/about/',
        'http://www.onlamp.com/pub/a/python/2003/04/17/metaclasses.html',
        'http://www.python.org/doc/',
        'http://www.python.org/download/',
        'http://www.python.org/getit/',
        'http://www.python.org/community/',
        'https://wiki.python.org/moin/',
        'http://planet.python.org/',
        'https://wiki.python.org/moin/LocalUserGroups',
        'http://www.python.org/psf/',
        'http://docs.python.org/devguide/',
        'http://www.python.org/community/awards/']
{% endhighlight%}


{% highlight python %}
tPool = ThreadPool(8)
{% endhighlight%}


{% highlight python %}
start_time = time.time()

results = tPool.map(request.urlopen, urls)
tPool.close()
tPool.join()

end_time = time.time()

elapsed = end_time - start_time

print("Elapsed is %s" % round(elapsed, 4))
{% endhighlight%}

    Elapsed is 1.346


### Benchmark:

- Pool 1: Elapsed is 4.481548070907593
- Pool 2: Elapsed is 2.9308207035064697
- Pool 4: Elapsed is 1.3849420547485352
- Pool 8: Elapsed is 1.1929352283477783


{% highlight python %}
round(2.222222222, 2)
{% endhighlight%}




    2.22




{% highlight python %}
results
{% endhighlight%}




    [<http.client.HTTPResponse at 0x1cf5ad880f0>,
     <http.client.HTTPResponse at 0x1cf5ad88128>,
     <http.client.HTTPResponse at 0x1cf5ad84a90>,
     <http.client.HTTPResponse at 0x1cf5ad8ada0>,
     <http.client.HTTPResponse at 0x1cf5ad8a550>,
     <http.client.HTTPResponse at 0x1cf5ad883c8>,
     <http.client.HTTPResponse at 0x1cf5ad88438>,
     <http.client.HTTPResponse at 0x1cf5ad887f0>,
     <http.client.HTTPResponse at 0x1cf5ada8c88>,
     <http.client.HTTPResponse at 0x1cf5ad84a58>,
     <http.client.HTTPResponse at 0x1cf5ad88470>,
     <http.client.HTTPResponse at 0x1cf5ad93160>,
     <http.client.HTTPResponse at 0x1cf5ad93b38>]




{% highlight python %}
url1 = results[0]

a = url1.read()

a
{% endhighlight%}