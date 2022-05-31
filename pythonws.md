layout: page
title: "Python worksop 01-06-2022"
permalink: https://datavkngs.github.io/pythonws
# Python workshop 01-06-2022

### Header 3

```markdown
Syntax highlighted code block

from setuptools import setup, find_packages

setup(
    name='example',
    version='0.1.0',
    description='Setting up a python package',
    packages=find_packages(include=['exampleproject', 'exampleproject.*']),
    install_requires=[
        'PyYAML',
        'pandas==0.23.3',
        'numpy>=1.14.5'
    ],
    extras_require={'plotting': ['matplotlib>=2.2.0', 'jupyter']},
    setup_requires=['pytest-runner', 'flake8'],
    tests_require=['pytest'],
    entry_points={
        'console_scripts': ['my-command=exampleproject.example:main']
    },
)
```
