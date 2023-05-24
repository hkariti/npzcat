# npzcat - look in NumPy files from the CLI

This is a utility for reading the contents of .npz and .npy files from the CLI.

The default operation is a summary of the contents. This works quickly on very large files too (based on a nice [SO answer](https://stackoverflow.com/a/68224674/949487)).

Requires a python environment that has `numpy`.

## Usage

```
$ time npz over_1gb_file.npz
Entry   Shape           Type
data    (1000000, 6508) int64
index   (1000000,)      object
columns (6508,)         object

real    0m0.361s
user    0m0.208s
sys     0m0.050s
```

You can print the content of a some entry (pass `-l` to avoid truncating):

```
$ npz -d index cellparams.npz
Entry   Shape           Type
data    (1000000, 4)    object
index   (1000000,)      object
columns (4,)            object

Contents of index:
['Cell1' 'Cell2' 'Cell3' ... 'Cell999998' 'Cell999999' 'Cell1000000']
```

WARNING: Printing an entry's contents reads the file with `allow_pickle=True` and may be a security issue.
