## Python

--------

### _PYTHONPATH_

For example, one has a code named `my_func.py` contains resuable
functions (e.g., `FUNCTION_1`, `FUNCTION_2`, ...).

For example, if one want to use `FUNCTION_1` from `my_func.py`
in any other code,

- old way

  If `my_func.py` does not exist in current working directory,

  - copy `my_func.py` to current working directory;

  - in new code, `from my_func import FUNCTION_1`.

- new way

  - put `my_func.py` under a directory, e.g., `/Users/hchen/code/reuse/python`;

  - in `~/.bashrc` (or `~/.bash_profile`), add
    ```bash
    export PYTHONPATH="${PYTHONPATH}:/Users/hchen/code/reuse/python"
    ```

    then

    ```
    source ~/.bashrc
    ```

  - now in new code, `from my_func import FUNCTION_1`.

--------

### [_matplotlib_](https://matplotlib.org/)

- __Change font to Times New Roman__

  - On Mac

    After Microsoft Office has been installed, simply add `Times New Roman`
    to `font.serif` and `font.sans-serif` in `matplotlibrc` file.

    It will look something like:
    <pre>
    font.serif      : <b>Times New Roman</b>, DejaVu Serif, Bitstream Vera Serif ...
    font.sans-serif : <b>Times New Roman</b>, DejaVu Sans, Bitstream Vera Sans ...
    </pre>

  - On Linux

    [dotfiles](https://github.com/hong-chen/dotfiles)

--------

### [_multiprocessing_](https://docs.python.org/3.6/library/multiprocessing.html)

Assume we have the following functions,

```python
def FUNCTION_1(a):
    print(a**2)

def FUNCTION_2(a, b):
    print(a+b)
```

<br><br>

> Use 8 processors to run `FUNCTION_1` by passing
> 0, 1, 2, ..., 7 to `a` to the function.

```python
import multiprocessing as mp

statements = np.arange(8)

pool = mp.Pool(processes=8)
pool.outputs = pool.map(FUNCTION_1, statements)
pool.close()
pool.join()
```
<br><br>

> Use 8 processors to run `FUNCTION_2` by passing
> 0, 1, 2, ..., 7 to `a` and 7, 6, 5, ..., 0 to `b`
> to the function.

First we need to modify `Function_2` to
```python
def FUNCTION_2(args):
    a, b = args
    print(a+b)
```

Then
```python
import multiprocessing as mp

a = np.arange(8)
b = np.arange(8)[::-1]

statements = zip(a, b)

pool = mp.Pool(processes=8)
pool.outputs = pool.map(FUNCTION_2, statements)
pool.close()
pool.join()
```
--------
