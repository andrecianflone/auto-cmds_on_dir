# auto-cmds_on_dir
Automatically call shell commands on directory entry. This is very useful,
especially when you want to automatically activate a python env when entering a
project root directory.

## Setup

Add the following to `.bash_aliases`
```
# This will automatically source .workspace when cd into a folder containing
# a file with that name
function workspace_cd() {
    cd $@ && [ -f ".workspace" ] && source .workspace
}

alias cd="workspace_cd"
```

Now any folder with a `.workspace` will have that file sourced. A sample below
to automatically activate conda env `env_name` on dir entry.
```
#!/bin/bash
# file .workspace

if [[ $CONDA_PREFIX != *"env_name"* ]]; then
    source activate t2t-sum
fi
```
## TODO
- Automatically append `.bash_aliases` with the function
