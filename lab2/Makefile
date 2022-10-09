.PHONY:pre,lexer,ast-gcc,ast-llvm,ir-llvm
pre:
	gcc mian.c -E -o main.i

lexer:
	clang -E -Xclang -dump-tokens main.c

ast-gcc:
	gcc -fdump-tree-original-raw  main.c
ast-llvm:
	clang -E -Xclang -ast-dump main.c
ir-llvm:
	clang -S -emit-llvm main.c -O0
arm:
	arm-linux-gnueabihf-gcc -o arm.s -S -O0 main.c -fno-asynchronous-unwind-tables
arm-test:
	arm-linux-gnueabihf-gcc -o arm.s -S -O0 main.c -fno-asynchronous-unwind-tables
	arm-linux-gnueabihf-gcc arm.s -o arm -static
	qemu-arm ./arm
test-my:
	arm-linux-gnueabihf-gcc test.s -o test -static
	qemu-arm ./test


