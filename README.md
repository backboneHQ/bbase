## bbase

### Config
Add the lines below at the end of `$HOME/.bashrc`:
```bash
# BACKBONE:
export BACKBONE_ROOT="/data/studio/backbone" # production release location
export BACKBONE_DEV_ROOT="$HOME/.backbone" # development release location
export BACKBONE_CORE_CONFIG="default" # "default" is an arbritary name for the config initialized by backbone
export BBASE_VERSION="stable" # release type (stable, beta and alpha)
source $BACKBONE_ROOT/core/bbase/$BBASE_VERSION/env
source $BACKBONE_ROOT/core/bbase/$BBASE_VERSION/init
```

### Overriding Versions
Overriding versions managed by bbase (BSYS, BVER, BLAUNCHER and BEVENTS):
```bash
# ...
source $BACKBONE_ROOT/core/bbase/$BBASE_VERSION/env
# it's done between 'env' and 'init'
export BVER_VESION="0.1.0"
export BLAUNCHER_VESION="0.1.0"
source $BACKBONE_ROOT/core/bbase/$BBASE_VERSION/init
```

Overriding versions managed by bver:
```bash
# ...
source $BACKBONE_ROOT/core/bbase/$BBASE_VERSION/init
# it's done after 'init'
export BVER_MAYATOOLS_VERSION="0.2.0"
```

### Activating the dev environment
In order to activate the dev env, so backbone can be aware about the resources
installed under "BACKBONE_DEV_ROOT", you need to run:
```bash
devenv
```

### Using/Testing bbase locally
Install bbase locally:
```bash
# enter in dev environment:
devenv
# run the installation:
./install
```

Make sure your backbone configuration is initializing bbase from BACKBONE_DEV_ROOT:
```bash
# backbone (dev bbase)
export BACKBONE_ROOT="/data/studio/backbone"
export BACKBONE_DEV_ROOT="$HOME/.backbone"
export BBASE_VERSION="alpha"
source $BACKBONE_DEV_ROOT/core/bbase/$BBASE_VERSION/env # <-
source $BACKBONE_DEV_ROOT/core/bbase/$BBASE_VERSION/init # <-
```

### Installing bbase for the first time
Make sure you have "jq" command installed, it can be download from:
https://stedolan.github.io/jq/download/

Also, bbase uses cmake for building/deployment
https://cmake.org

### Installing bbase
The instructions below are also applicable for all core & core-settings installs.

A) Deploying under the development area (only affects you):
```bash
./binstall
# the deployed version is only available under dev environment. Therefore, in case you want to activate it run:
devenv
```

B) Deploying under the production area (by default it only deploys the version data where this version is NOT linked to any release type. Since linking to release type can be done later):
```bash
./binstall --production
```
