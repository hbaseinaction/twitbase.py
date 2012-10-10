# HBase In Action: Thrift TwitBase client in Python

[http://www.manning.com/dimidukkhurana][0]

## Using the Python TwitBase client

The client assumes you have an existing TwitBase schema containing
User data. It also requires a running thrift gateway. Start a gateway
against your HBase cluster with:

    $ hbase thrift start

Launching the client is then as simple as:

    $ ./TwitBase.py list

You can also interact with the embedded HBase client from within an
interactive python session. For instance, you can list the available
HBase tables like this:

    $ python
    Python 2.7.1 (r271:86832, Jul 31 2011, 19:30:53)
    ...
    >>> from thrift.transport import TSocket
    >>> from thrift.protocol import TBinaryProtocol
    >>> from hbase import Hbase
    >>> transport = TSocket.TSocket('localhost', 9090)
    >>> protocol = TBinaryProtocol.TBinaryProtocol(transport)
    >>> client = Hbase.Client(protocol)
    >>> transport.open()
    >>> client.getTableNames()
    ['followers', 'twits', 'users']

## License

Copyright (C) 2012 Nick Dimiduk, Amandeep Khurana

Distributed under the [Apache License, version 2.0][1], the same as HBase.

[0]: http://www.manning.com/dimidukkhurana
[1]: http://www.apache.org/licenses/LICENSE-2.0.html
