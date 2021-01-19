```sh
cargo new led
cd led
cargo new auxiliary --lib

cargo search cortex-m
cargo search panic-halt
cargo search cortex-m-rt
cargo search f3



cargo clean
cargo build --target thumbv7em-none-eabihf
# Finished dev [unoptimized + debuginfo] target(s) in 1m 11s

cargo build --release --target thumbv7em-none-eabihf
#  Finished release [optimized] target(s) in 2m 02s
# Finished release [optimized] target(s) in 1m 49s

file led
# led: ELF 32-bit LSB executable, ARM, EABI5 version 1 (SYSV), statically linked, with debug_info, not stripped
# 597K

arm-none-eabi-size led
#    text    data     bss     dec     hex filename
#    4640       0       4    4644    1224 led

openocd -f interface/stlink.cfg -f target/stm32f3x.cfg

arm-none-eabi-gdb -q led
target remote :3333
load
continue

```