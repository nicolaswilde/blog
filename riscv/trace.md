# trace memory & regfile behavior

code example.c (whatever, or .S), use riscv64-unknown-elf-gcc to compile

    riscv64-unknown-elf-gcc -o example example.c

use riscv64-unknown-elf-run to run elf file and trace

    riscv64-unknown-elf-run example --trace-memory=on --trace-register=on
