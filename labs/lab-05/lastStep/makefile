all: dyn stat
clean:
	rm dyn stat program.o dynlib.so statlib.a source/block.o
dyn: program.o dynlib.so
	cc program.o dynlib.so -o dyn -W1, -rpath .
stat: program.o statlib.a
	cc program.o statlib.a -o stat
program.o: program.c
	cc -c program.c -o program.o
statlib.a: source/block.o
	ar qc statlib.a source/block.o
dynlib.so: source/block.o
	cc -shared -o dynlib.so source/block.o
source/block.o: source/block.c
	cc -fPIC -c source/block.c -o source/block.o
