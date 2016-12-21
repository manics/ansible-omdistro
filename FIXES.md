To workaround this error:

```
# omd start
Doing 'start' on site local:
Starting mkeventd...Traceback (most recent call last):
  File "/omd/sites/local/bin/mkeventd", line 398, in <module>
    from pymongo.connection import Connection
  File "build/bdist.linux-x86_64/egg/pymongo/__init__.py", line 80, in <module>
  File "build/bdist.linux-x86_64/egg/pymongo/connection.py", line 39, in <module>
  File "build/bdist.linux-x86_64/egg/pymongo/mongo_client.py", line 38, in <module>
  File "/usr/lib64/python2.7/random.py", line 49, in <module>
    import hashlib as _hashlib
  File "/omd/sites/local/lib/python/hashlib.py", line 115, in <module>
    f()
TypeError: 'frozenset' object is not callable
OK
Starting rrdcached...Already running.
npcd already started...
Starting nagios...Already running.
Starting dedicated Apache for site local...(already running)...OK
Initializing Crontab...OK
```

Replace hashlib.py (https://monitoring-portal.org/index.php?thread/34786-hashlib-problem-rhel-7-2-maipo-oel-7-2/):

    cp /usr/lib64/python2.7/hashlib.py /omd/versions/1.30/lib/python/hashlib.py
