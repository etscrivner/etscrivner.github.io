---
layout: post
title:  "Python Configurations Done Right"
date:   2014-06-25 22:27:00 -0800
categories: software
---
If you're building web applications then I hope that you're following the [Twelve-Factor App](http://12factor.net) approach. If so you will be [storing your config in the environment](http://12factor.net/config) and for most of you that means in environment variables.

This approach has a few benefits over storing them in yaml, ini, json, etc. Firstly, it stops you from commiting sensitive information into version control - which it kind of feels weird even saying you should be using if you're not. Secondly, it allows your configuration to vary substantially across deployments - something it will inevitably have the tendency to do.

Now if you're following this approach then the question inevitably arises as to how you're going to execute the app with a given configuration when you run it from the command-line. The following is a simple solution invented with some help from my colleagues at [plug.dj](http://plug.dj) (EDIT: [Jon](http://rustyrazorblade.com) pointed out to me we were doing something similiar at [SHIFT](http://shift.com)) - just write a simple shell script for every environment you deploy to like so:

```sh
#!/bin/sh
export MY_APP_NAME=superslice
export MY_APP_AWS_KEY=super-secret
export MY_APP_AWS_SECRET_KEY=super-super-secret
# Finally, call whatever command comes after this
$*
```

For those who don't know $* is simply the
[ARGLIST](http://www.tldp.org/LDP/abs/html/internalvariables.html#ARGLIST) - the
list of arguments passed into the application. The usage will make more sense
once you see it in action below.

Now we just need to hook our application into a simple system for reading
these environment variables. This would look something like the following:

```python
import os


# Configuration variable names as constants
APP_NAME = 'MY_APP_NAME'
APP_AWS_KEY = 'MY_APP_AWS_KEY'
APP_AWS_SECRET_KEY = 'MY_APP_AWS_SECRET_KEY'


class Config(object):

    def __init__(self, config=None):
        """Initialize config with mapping.
        :param config: (Defaults to os.environ) A dict-like config object.
        :type config: dict
        """
        self.config = config if config else os.environ

    def get(self, key, default=None):
        return self.config.get(key, default)

    def get_bool(self, key, default=False):
        return self.config.get(key, str(default)).lower() in ('true', 't', '1')
```

Finally, we can grab environment variables and begin using them in our
application.

```python
import sys

import config


if __name__ == '__main__':
    cfg = config.Config()
    print 'Welcome to {}'.format(cfg.get(config.APP_NAME))
    print sys.argv
```

Then when it comes time to run your application simply prepend the shell script.

```
user@computer:~/app$ ./localsettings.sh bin/app.py --app-arg1 arg1-val --app-arg2
Welcome to superslice
['bin/app.py', '--app-arg1', 'arg1-val', '--app-arg2']
```
