## Basics

<!--- 
file:///C:/Users/htorres/Downloads/978-3-642-37009-0_2.pdf 
https://github.com/dchirila/imf_ess
-->

```fotran
program hello_world
  implicit none
  print *, " Hello, world of Modern Fortran!"
end program hello_world
```

The `implicit none` entry, which instructs the compiler to ensure all used 
variables are of an explicitly defined type. It is strongly recommended to 
include this statement at the beginning of each program. The same advice will 
apply to modules and procedures (discussed later).

The `−fimplicit−none` flag can be used, in principle, in `gfortran`, but 
this is also discouraged because it introduces an unnecessary dependency on 
compiler behavior.

Comments: Commenting the nontrivial aspects of your code is highly recommended. 
In Fortran, this is achieved by typing an exclamation mark (`!`).

Multi-line statements: Unlike languages from the C-family, in Fortran the semicolon
`;` for marking the end of a statement is optional (although it is still used sometimes,
to pack several short statements on the same line). By default, the end of the line
is also considered to be the end of the statement. A line of code in Fortran should
be at most 132 characters long. If a statement is so long that this is not sufficient
(for example, a long formula for evaluating derivatives in finite-difference numerical
schemes), we can choose to continue it on the following line(s), by inserting an
ampersand `&` at the end of each line that is continued. Since Fortran 2003, up to
255 continuation lines are allowed for any statement.

The two possible uses of continuation lines are shown in the example below:

```fortran
program continuation_lines
  implicit none
  integer :: seconds_in_a_day = 0

  ! Normal continuation-lines
  seconds_in_a_day = &
       24*60*60 ! 86400

  print*, seconds_in_a_day

  ! Continuation-lines with a split integer-literal token
  seconds_in_a_day = 2&
       &4*60*60 ! still 86400. In this case, splitting the '24'
                ! is unwise, because it makes code unreadable.
                ! However, for long character strings this can be
                ! useful (see below).
  print*, seconds_in_a_day

  ! Continuation-lines with a split string token.
  print*, "This is a really long string, that norma&
       &lly would not fit on a single line."
end program

```
