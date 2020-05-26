# Installation Guide for `q`

Normal download and installation visit [here](https://kx.com/connect-with-us/download/).

You may request [academic license](https://kx.com/connect-with-us/kx-academic-program/) (not necessary).

I installed the `q` with a machine-learning environment setup.

### Download `jupyterq` via Anaconda

> Jupyter kernel for kdb+ introduction: https://code.kx.com/q/ml/jupyterq/

<img src="https://i.imgur.com/pUdS8dq.png" width=800 alt="kdb kernel" />

The three Kx packages can be downloaded from [anaconda.org/kx](https://anaconda.org/kx):

- `kdb`
- `embedpy`
- `jupyterq`

These are available for Linux, Windows and macOS.

They are in a dependency tree. 
```
- jupyterq
  - embedpy
    - kdb
```

So we use command
```bash
conda install -c kx jupyterq
```
Before starting q, run the following commands:
```bash
source deactivate base
source activate base
```

When you first run `q` it will ask for your name and email for generating license.


### Install `rlwrap`

Call kdb+ within the `rlwrap` command, which will allow you to call back and edit previous lines.

Use homebrew to install `rlwrap`
```bash
brew install rlwrap
```
Verify installation. Type command to see the version of rlwrap if installed successfully.
```bash
rlwrap -v
```

### Add `q` alias to bash profile

Define `q` as a command alias, allowing you to invoke kdb+ without specifying the path to it.

Use vim or IDE of your choice to open `~/.bash_profile`:
```bash
vim ~/.bash_profile
open -a "Sublime Text" ~/.bash_profile
```
append the following line
```bash
alias q='QHOME=~/anaconda3/q rlwrap -r ~/anaconda3/q/m64/q'
```

and save it. Start a new Terminal session, or tell Bash to use the revised profile:

```bash
source ~/.bash_profile
```

### Confirm successful installation
Type q in Terminal and hit enter. 

Now you can type an expression and recall it using the up-arrow key.

```bash
q)til 6 / first 6 integers
0 1 2 3 4 5
q)til 6 / first 6 integers
0 1 2 3 4 5
q)\\
$
```

