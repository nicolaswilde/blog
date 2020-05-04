# build riscv-tests

## compile all 32/64 tests

    cd riscv-tests/isa
    make

## compile RV32I testbench

    cd riscv-tests/benchmarks

modify riscv-tests/benchmarks/Makefile: XLEN ?= 32

test mm, mt-vvadd, and mt-matmul will cause error using riscv32-unknown-elf- toolchain, thus remove these test

    make

# test using spike

    spike --isa=RV32I dhrystone.riscv

# get trace

    spike -l --isa=RV32I  dhrystone.riscv 2> spike.log

# Reference

https://github.com/ucb-bar/riscv-sodor
