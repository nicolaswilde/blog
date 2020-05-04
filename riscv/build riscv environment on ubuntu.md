# RISCV tools

    git clone https://github.com/riscv/riscv-tools.git  
    cd riscv-tools  
    git submodule update --init --recursive

# RISCV toolchain

## download

    git clone --recursive https://github.com/riscv/riscv-gnu-toolchain

This step will take long time (several days for me, bad github usage experience in China), git clone about 5 GB data.

Can use gitee to speed up, but need to add each submodule separately

One submodule 'boringssl' is stored on google server, need VPN to clone it from China. I git clone it on a abroad server then scp to my computer.

## dependency

    cd riscv-gnu-toolchain
    sudo apt-get install autoconf automake autotools-dev curl libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev libnewlib-dev

## build

    INSTALL_PATH='/opt/riscv'
    export PATH=$PATH:$INSTALL_PATH/BIN
    ./configure --prefix=$INSTALL_PATH (can use --with-arch=rv32i to build riscv32-unknown-elf- toolchain)
    sudo make

## path

    sudo gedit ~/.bashrc
    export PATH=/opt/riscv/bin:$PATH
    export RISCV=/opt/riscv

then you can test:

    riscv64-unknown-elf-gcc -o hello hello.c

# spike & pk

open terminal in /riscv-tools/riscv-isa-sim

    apt-get install device-tree-compiler
    mkdir build
    cd build
    ../configure --prefix=$RISCV
    make
    sudo make install

open terminal in /riscv-tools/riscv-pk

    mkdir build
    cd build
    ../configure --prefix=$RISCV --host=riscv64-unknown-elf
    make
    make install

then you can test:

    spike pk hello

print "hello world" means success!!!

# reference

https://blog.csdn.net/shensen0304/article/details/95504258
