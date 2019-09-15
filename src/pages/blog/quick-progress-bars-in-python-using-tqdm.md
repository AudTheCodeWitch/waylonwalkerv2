---
templateKey: blog-post
path: tqdm-quick-progress-bar-python
title: Quick Progress Bars in python using TQDM
date: 2019-09-18T05:00:00.000+00:00
status: published
description: Quick Progress Bars in python using TQDM
cover: "/images/markus-spiske-7CjegTgBPKc-unsplash.jpg"
twitter_cover: "/images/markus-spiske-7CjegTgBPKc-unsplash.jpg"

---
tqdm is one of my favorite general purpose utility libraries in python.  It allows me to see progress of multipart processes as they happen.  I really like this for when I am developing something that takes some amount of time and I am unsure of performance.  It allows me to be patient when the process is going well and will finish in sufficient time, and allows me to 💥 kill it and find a way to make it perform better if it will not finish in sufficient time.

![](/images/tqdm2.gif)
_for more gifs like these follow me on twitter [@waylonwalker](https://twitter.com/_WaylonWalker)_

**Add a simple Progress bar!**
```
from tqdm import tqdm
from time import sleep

for i in tqdm(range(10)):
	sleep(1)
```

**convenience**

TQDM also has a convenience function called trange that wraps the range function with a tqdm progress bar automatically.

```
from tqdm import trange
from time import sleep

for i in trange(range(10)):
	sleep(1)
```


**notebook support**

There is also notebook support.  If you are bouncing between ipython and jupyter I recomend importing from the auto module.

```
from tqdm.auto import tqdm
from time import sleep

for i in tqdm(range(10)):
	sleep(1)
```