<h1>Simple Website Crawler</h1>
<br>ref:https://gist.github.com/rascundampelcuf/663efb4f6c436d57492a7b967896f5e3#simple-website-crawler

The following repo is an extract of the article Building a simple crawler. It allows crawling from a URL and for a given number of bounce.

<h2>Basic Usage</h2>


<br>from crawler import Crawler
<br>crawler = Crawler()
<br>crawler.crawl('http://techcrunch.com/')
<br># displays the urls
<br>print crawler.content['techcrunch.com'].keys()



<h2>Advanced Usage</h2>
The following is using a cache (in sqlalchemy, crawler.db) and crawl to a depth of 3 from the home page. The no_cache parameter prevent '/' to be cached, enforcing new pull of the homepage each time the crawler is launched.


<br>import re
<br>from crawler import Crawler, CrawlerCache 
<br>crawler = Crawler(CrawlerCache('crawler.db'), depth=3) 
<br>crawler.crawl('http://techcrunch.com/', no_cache=re.compile('^/$').match) 
<br># displays the urls 
<br>print crawler.content['techcrunch.com'].keys() 

