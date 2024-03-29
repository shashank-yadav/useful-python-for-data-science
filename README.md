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

4. **Using collections.defaultdict(datatype)**  
Better than using normal python dicts

5. **Making use of dotmap for configs**  
Use [dotmap](https://pypi.org/project/dotmap/) instead of dict for configs and other stuff. It's way more cleaner:
```python
from dotmap import DotMap
m = DotMap()
m.name = 'Joe'
print('Hello ' + m.name)
# Hello Joe
```
6. **Hyperparameter Tuning**  
Use [hyperopt](https://medium.com/district-data-labs/parameter-tuning-with-hyperopt-faa86acdfdce) for hyperparameter tuning. Following is a motivating example, find detailed info [here](https://github.com/hyperopt/hyperopt/wiki/FMin)
```python
from hyperopt import fmin, tpe, hp
best = fmin(
    fn=lambda x: x,
    space=hp.uniform('x', 0, 1),
    algo=tpe.suggest,
    max_evals=100)
print best
```
A slightly more general example:  
```python
from hyperopt import fmin, tpe, hp, STATUS_OK, Trials

space = {
    'x': hp.uniform('x', 0, 1),
    'y': hp.uniform('y', 0, 1)
}

def score(params):
    x = params['x']
    y = params['y']
    return {'loss': (0.5 - x*y)**2, 'status': STATUS_OK }

trials = Trials()
best = fmin(score, space, algo=tpe.suggest, trials=trials, max_evals=100)
print(best['x'], best['y'])
```
