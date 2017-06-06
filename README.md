# wokec

Wokec is a sufficiently advanced compiler that can see the ultimate, universal
effects of a function's or a program's execution and optimizes it accordingly
to reasonably fast enough code that accomplishes the same goal.

## Theory

Let's take a simple function in Lisp.  Scheme to be precise.

```scheme
(define (fib n)
  (if (> n 1)
      (+ (fib (- n 1))
         (fib (- n 2)))
      1))
```

This is a simple Fibbonacci function.  Does it have any side effects?  No.
Does it have any error cases?  Other than potentially overflowing the stack,
no.  So if it's entirely self-contained, and we didn't store the return value,
then we can safely optimize the entire call away.

Now what if we consider our program as a function that takes inputs N and
returns output R.  In this case, N is the state of the universe before the
execution, and R is the state of the universe after it.  Since N and R are so
utterly large, and difference between the two of them is comically close to
zero.  Therefore it's safe to optimize away effectively the entire execution of
the compiled program.

## Supported Languages

* all of them

## Usage

```
./wokec <input> [-o <output>]
```

