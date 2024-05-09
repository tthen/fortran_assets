## General Concepts

The compiler is invoked, passing the created file as an argument. In Linux, using 
`gfortran`, this would be achieved by typing the following command in a terminal window: 

```terminal
gfortran -c myprogram.f90
```

At this point, an additional file (`myProgram.o`) will be created. This contains 
machine code generated from myProgram.f90 which does not contain, however, any code 
for libraries that may be needed by your program. It is the job of the linker to 
find the missing pieces and to produce the final, executable file. In Linux, the 
GNU linker (`ld`) is normally used for this purpose. For simplicity, it is better 
to perform the linking stage also through the compiler, which will call the linker 
with the appropriate options in the background:

```terminal
gfortran -o myprogram.f90 myprogram.o
```

This step will create the executable program, which can be run with the command: 

```terminal
./myprogram.o
```
Compiling and linking in one step. 

```terminal
gfortran -o myprogram myprogram.f90 
```
