# 1. Create a python package

[A Practical Guide to Using Setup.py](https://godatadriven.com/blog/a-practical-guide-to-using-setup-py/)

*Commands*
```markdown
python -m venv .venv
source .venv/..
touch README.md
touch .gitignore
mkdir src
cd src
mkdir exampleproject
vim setup.py
vim requirements.txt
cd exampleproject
touch __init__.py
touch example.py
pip install -e .
```
*Example setup.py*
```markdown
import os
from setuptools import setup, find_packages

with open('requirements.txt') as f:
    required = f.read().splitlines()

setup(
    name='example',
    version='0.1.0',
    description='Setting up a python package',
    packages=find_packages(include=['exampleproject', 'exampleproject.*']),
    install_requires=required,
    extras_require={'plotting': ['matplotlib>=2.2.0', 'jupyter']},
    setup_requires=['pytest-runner', 'flake8'],
    tests_require=['pytest'],
    entry_points={
        'console_scripts': ['my-command=exampleproject.example:main']
    },
)
```

*Example requirements.txt*
```markdown
black==22.3.0
mypy==0.960
pylint==2.13.9
pytest==7.1.2
pandas==0.23.3
numpy>=1.14.5
```

# 2. Python style guide and code formatting

[PEP 8 – Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008)

```markdown
# validation
pip install pylint
pylint /src
# formatting
pip install black
black /src
```

# 3. Check type consistency

[PEP-484 - Type hints](https://www.python.org/dev/peps/pep-484)\
[PEP-526 – Syntax for Variable Annotations](https://www.python.org/dev/peps/pep-526)\
[PEP 3107 – Function Annotations](https://www.python.org/dev/peps/pep-3107)

```markdown

Mwh = float

def get_mwh_estimate_from_park(parkname: str, mwp: float) -> Mwh
    print(parkname)
    print(mwp)
    return mwp * 0.5

mwh_est = get_mwh_estimate_from_park("Amsterdam", "Ten")

```

# 4. Unit testing

```markdown
pip install pytest
mkdir tests
cd tests
vim test_predict.py

from package_xyz import function_xyz

def test_predict():
    assert 1 == function_xyz()


pytest tests/
```

# 5. Makefile

*Example Makefile*
```markdown
.PHONY: typehint
typehint:
	mypy --ignore-missing-imports src/

.PHONY: test
test:
	pytest tests/

.PHONY: lint
lint:
	pylint src/

.PHONY: checklist
checklist: lint typehint test

.PHONY: black
black:
	black -l 79 *.py 
```

Execute with make black or make checklist

# Bonus

[PEP 557 – Data Classes](https://www.python.org/dev/peps/pep-557) \
[PEP 585 – Type Hinting Generics In Standard Collections](https://www.python.org/dev/peps/pep-585)
