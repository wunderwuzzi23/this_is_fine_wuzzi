# Welcome to this_is_fine_wuzzi

Basic PyPi package that runs a command upon `pip download` or `pip install`.

## Explanation

The `setup.py` file contains the info to run a custom command which will be triggered upon `pip download` or `pip install` of the package.

This basic example just prints: `print("Hello, p0wnd!")`


## Build the package

```
python -m build
```

This will create a `./dist/` folder containing the wheel `whl` and `tar.gz` files.

### Pre-requisites

In case you encounter errors building, make sure to have `setuptools` and `build` packages installed.

```
pip install setuptools
pip install build
```


## Host the package in pypi-server

One option to test and host the package yourself is using `pypi-server`, e.g `pip install pypiserver`. 
Then you can run a server with:

```
pypi-server run -v -p 8080 ./packages
```

And finally copy the tar.gz file to your pypi-server's `./packages` folder.

## Download or Install the package

Now it's possible to trigger the extra command by either downloading or installing the package:

```
pip download this_is_fine_wuzzi --index-url http://localhost:8080 -v
```

This will run the custom script and print `Hello, p0wnd!` out. 
Note:Any messages printed out to the console won't be displayed by pip, unless you specify `-v`.

That's it for the basic repo.

Very important to be aware of!

## Mitigations

The `setup.py` is only executed if the package is in `tar.gz` format. So, either reviewing the tar file or making sure there is a wheel file (`.whl`) present and used.

You can enumerate the offered packages via `https://packagemanager/simple/<package-name>`.

This way one can see what files are hosted for the package (tar or wheel, or both), and download (e.g. `wget`) and inspect the `tar.gz` file if that is the only option.


## References

Learned that this issue first via Security Now! Podcast which pointed to this post from Checkmarx:

* Checkmarx: [Automatic Execution of Code Upon Package Download on Python Package Manager](https://medium.com/checkmarx-security/automatic-execution-of-code-upon-package-download-on-python-package-manager-cd6ed9e366a8)
* Blog Post on [Embrace The Red](https://embracethered.com/blog/posts/2022/python-package-manager-install-and-download-vulnerability/)
* https://pypi.org/project/pypiserver/

