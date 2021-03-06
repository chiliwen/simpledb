### simpledb

Miniature [Redis](https://redis.io)-like database written in Python.

#### running

by default, the simpledb server runs on localhost:31337.

the following options are supported:

```
Usage: simpledb.py [options]

Options:
  -h, --help            show this help message and exit
  -d, --debug           Log debug messages.
  -e, --errors          Log error messages only.
  -t, --use-threads     Use threads instead of gevent.
  -H HOST, --host=HOST  Host to listen on.
  -m MAX_CLIENTS, --max-clients=MAX_CLIENTS
                        Maximum number of clients.
  -p PORT, --port=PORT  Port to listen on.
  -l LOG_FILE, --log-file=LOG_FILE
                        Log file.
  -x EXTENSIONS, --extension=EXTENSIONS
                        Import path for Python extension module(s).
```

to run with debug logging on port 31339, for example:

```
$ simpledb.py -d -p 31339
```

#### usage

the server is capable of storing the following data-types natively:

* strings and/or binary data
* numerical values
* null
* lists (may be nested)
* dictionaries (may be nested)

```python

from simpledb import Client

client = Client()
client.set('key', {'name': 'Charlie', 'pets': ['mickey', 'huey']})

print(client.get('key'))
{'name': 'Charlie', 'pets': ['mickey', 'huey']}
```
