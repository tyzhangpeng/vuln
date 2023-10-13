# SEGV swftools/lib/modules/swfshape.c:1094:16 in free_lines

## project address

https://github.com/matthiaskramm/swftools

## info

OS：Ubuntu20.04 TLS
CFLAGS="-g -fsanitize=address" CXXFLAGS="-g -fsanitize=address" LDFLAGS="-g -fsanitize=address" ./configure --disable-shared

## poc

https://github.com/tyzhangpeng/vuln/blob/main/free_lines/id%3A000053%2Csig%3A11%2Csrc%3A000866%2Ctime%3A234353%2Cexecs%3A126696%2Cop%3Ahavoc%2Crep%3A4

## ASAN Info

```
=================================================================
==1596878==ERROR: AddressSanitizer: SEGV on unknown address 0x000000000020 (pc 0x000000542e03 bp 0x7fff452e5ac0 sp 0x7fff452e5910 T0)
==1596878==The signal is caused by a READ memory access.
==1596878==Hint: address points to the zero page.
    #0 0x542e03 in free_lines /home/ubuntu/fuzz/swftools/swftools/lib/modules/swfshape.c:1094:16
    #1 0x542bd8 in swf_RecodeShapeData /home/ubuntu/fuzz/swftools/swftools/lib/modules/swfshape.c:1122:5
    #2 0x4db13e in s_filled /home/ubuntu/fuzz/swftools/swftools/src/swfc.c:1285:5
    #3 0x4f9af7 in c_primitive /home/ubuntu/fuzz/swftools/swftools/src/swfc.c:3855:22
    #4 0x4ee709 in parseArgumentsForCommand /home/ubuntu/fuzz/swftools/swftools/src/swfc.c:4475:5
    #5 0x4ee709 in main /home/ubuntu/fuzz/swftools/swftools/src/swfc.c:4598:2
    #6 0x7f8b22da9082 in __libc_start_main /build/glibc-SzIz7B/glibc-2.31/csu/../csu/libc-start.c:308:16
    #7 0x41d63d in _start (/home/ubuntu/fuzz/swftools/swftools/src/swfc+0x41d63d)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV /home/ubuntu/fuzz/swftools/swftools/lib/modules/swfshape.c:1094:16 in free_lines
==1596878==ABORTING
```
