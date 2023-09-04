# misspy
![Supported Python Version](https://img.shields.io/pypi/pyversions/misspy) [![PyPI version](https://badge.fury.io/py/misspy.svg)](https://badge.fury.io/py/misspy) [![PyPI Downloads](https://img.shields.io/pypi/dm/misspy.svg)](https://badge.fury.io/py/misspy) [![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

Misskey API library for Python with StreamingAPI support.

# supported software
Misskey forks other than [misskey-dev/misskey](https://github.com/misskey-dev/misskey) are __***basically***__ only the latest versions are supported.
* [misskey](https://github.com/misskey-dev/misskey)
* [misskey (misskey.io)](https://github.com/misskeyIO/misskey)
<!-- * [firefish (calckey)](https://codeberg.org/firefish/firefish) (under development) -->


## supported misskey versions
> MiAuth is not supported before 12.27.0.

| version               | support | MiAuth | 
| :-------------------: | ------- | -----: | 
| v11 before (and fork) |  ❌ |    ❌  | 
| v12.27.0 before       |  ⭕   |   ❌   | 
| v12.27.0 later       |   ⭕  |  ⭕  | 
| v13 later             |  ⭕   |  ⭕  | 


# example
**Other examples can be found in the examples directory.**

## send note
```python
import misspy

mi = misspy.Bot(address, i=token)
```

## Output notes text to the console
```python
import misspy
from misspy.ext import MiAuth


class StreamingBot(misspy.Bot):
    async def on_ready(self):
        print("running")

    async def on_note(self, message):
        print("------------")
        print(message.text)
        print("------------")


bot = StreamingBot("misskey.io", i=token)
bot.run()
```

## MiAuth
```python
from misspy.ext import MiAuth

mia = MiAuth("misskey.io")
print(mia.generate_url("example app"))
while True:
    input("enter to continue...")
    try:
        token = mia.check()
        break
    except misspy.MiAuthFailed:
        pass
print(token)
```


# docs
Document is Multi-Language supported. (English, 中文, Español (lengua), 한국어, 日本語)

Documentation can be found at:
https://misspy.sonyakun.xyz/
