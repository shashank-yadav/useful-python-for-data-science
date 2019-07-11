# useful-python-for-data-science
Some useful stuff to improve execution of data science experiments in python

1. **Making use of Multiprocessing**
Always try to make the best use of your multiple cores:
```python
from multiprocessing import Pool

# Mapping to obtain iterators
it = pool.imap(f, range(10))
it = pool.imap_unordered(f, range(10))

# Mapping to obtain lists
l = pool.map(f, range(10))
l = pool.map_unordered(f, range(10))
```
2. **Making use of itertools**
Iterators are extremely efficient and really helpful when you need to iterate over large sequences. Go through the [documentation](https://docs.python.org/2/library/itertools.html) to know more

3. **Using glob**
Make use of glob when you need to read several files whose names follow a regexp

4. **Using collections.defeautdict(datatype) instead of normal python dict**
