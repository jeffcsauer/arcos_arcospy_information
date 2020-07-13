The following form is used to organize the submission of bug reports to the `arcos` and `arcospy` software.  When submitting a bug report, please include the following information:

- Software: are you using R or Python?

- Python information:
```python
>>> import os; print(os.name, os.sys.platform)
>>> import sys; print(sys.version)
>>> import arcospy; print(arcospy.__version__)
```

- R information:
```r
sessionInfo()
packageVersion("arcos")
```

* Bug information
    - What arcos/arcospy commands are you using?
    - Please paste a reproducible example of the bug you are encountering.


After crafting your report, feel free to delete this template text.