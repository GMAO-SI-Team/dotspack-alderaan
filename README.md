# dotspack for Alderaan

This is a collection of .spack files for Alderaan

## Environmental Settings

I currently have set in .bashrc:

### All times

```
OS_VERSION=$(grep VERSION_ID /etc/os-release | cut -d= -f2 | cut -d. -f1 | sed 's/"//g')

export SIPROJ=/discover/nobackup/projects/gmao/SIteam
export SPACK_ROOT=$SIPROJ/spack
```

The `OS_VERSION` is used to distinguish between SLES15 and SLES12.

### On prompt

Note here we need to make a distinction between the OS versions on discover. At the moment,
all tests have been done on the SLES15 machine.

```
   export SPACK_SKIP_MODULES=1
   if [[ "$OS_VERSION" == "15" ]]; then
      export SPACK_PYTHON=/usr/local/other/GEOSpyD/23.5.2-0_py3.11/2023-11-02/bin/python3
   fi
   . $SPACK_ROOT/share/spack/setup-env.sh


   if [[ "$OS_VERSION" == "15" ]]; then
      module use -a $SPACK_ROOT/share/spack/lmod/linux-sles15-x86_64/Core
   fi
```

### Needed brew packages

These are based on those from spack-stack

```bash
brew install coreutils
brew install gcc@12
brew install git
brew install git-lfs
brew install lmod
brew install wget
brew install bash
brew install curl
brew install cmake
brew install openssl
brew install qt@5
brew install mysql
```

### config.yaml

Note that to keep the build and misc caches out of the home directory, I have set:

```yaml
  build_stage: /discover/nobackup/projects/gmao/SIteam/spack-cache/stage
  misc_cache: /discover/nobackup/projects/gmao/SIteam/spack-cache/misc
```
