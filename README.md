# Welcome to this_is_fine_wuzzi

Basic PyPi package that runs a command upon `pip download` or `pip install`.

## Explanation

The `setup.py` file contains the info to run a custom command which will be triggered upon `pip download` or `pip install` of the package.

This basic example just prints: `print("Hello, p0wnd!")`


## Build the package

```
python -m build
```

This will create a `./dist/` folder containing the wheel and tar.gz files.

## Host the package in pypi-server

One option to test and host the package yourself is using `pypi-server`.

```
pypi-server run -v -p 8080 ./packages
```

And finally copy the tar.gz file to your pypi-server's `./packages` folder.

## Download or Install the package

```
pip download this_is_fine_wuzzi --index-url http://localhost:8080 -v
```

Any messages printed out to the console won't be displayed, unless you specify `-v`.

## References

Learned that this issue first via Security Now Podcast which pointed to this post from Checkmarx:

* Checkmarx: [Automatic Execution of Code Upon Package Download on Python Package Manager](https://medium.com/checkmarx-security/automatic-execution-of-code-upon-package-download-on-python-package-manager-cd6ed9e366a8)
* Blog Post on [Embrace The Red](https://embracethered.com/blog/posts/2022/python-package-manager-install-and-download-vulnerability/)

