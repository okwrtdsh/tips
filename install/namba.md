# how to install numba on osx
```
brew install homebrew/versions/llvm37 --with-rtti
git clone https://github.com/numba/llvmlite
cd llvmlite
LLVM_CONFIG=/usr/local/Cellar/llvm37/3.7.1/bin/llvm-config-3.7 python setup.py install
LLVM_CONFIG=/usr/local/Cellar/llvm37/3.7.1/bin/llvm-config-3.7 pip install numba
rm -rf llvmlite
```

http://stackoverflow.com/questions/36385785/error-installing-numba-on-os-x
