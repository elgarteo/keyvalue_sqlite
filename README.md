# KeyValueSqlite

Super easy drop in replacement for python dictionary, which stores
it's key-value to an sqlite database.

# API

```
from keyvalue_sqlite.keyvalue_sqlite import KeyValueSqlite

DB_PATH = '/path/to/db.sqlite'

db = KeyValueSqlite(DB_PATH, 'table-name')
# Now use standard dictionary operators
db.set_default('0', '1')
actual_value = db.get('0')
assert '1' == actual_value
db.set_default('0', '2')
assert '1' == db.get('0')
```

This datastructure is not going to win any performance races, but it
is super simple to use with just a few lines of code. This is a great
option for one of those small web apps which doesn't have enough load
to justify mysql or postgres, or a file that will be used by multiple
processes, or to store a file that can't be corrupted during a power
failure.

When fetching large amounts of data try to use get_many() or dict_range().

# Links
  * https://pypi.org/project/keyvalue-sqlite
  * https://github.com/zackees/keyvalue_sqlite

# TODO:
  * Make read access use a shared lock rather than an exclusive lock.
