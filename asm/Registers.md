#What are Registers in Assembly

Registers are a little intimidating when you first start coding in Assembly.
They pretty much hold whatever you want them to hold, and they have weird 
naming patterns that correlate with their sizes.

## Registers in x86

<img src="https://i.imgur.com/e7j0c5E.png" width="500"/>

### What do we do with registers?

Registers are used to store and interact with values. For example, if you
want to add numbers, you can do so by using registers and performing operations

```asm
mov rax, 5 ; copy 5 to rax register
mov rbx, 25 ; copy 25 to rbx register
add rax, rbx ; add values in rax and rbx together and store in rax
```

Now if you were to print rax or inspect rax in a debugger, you can see the result
of that addition in the rax register: **30**

_Side Note: if you want to inspect a value in gdb, type `p/d $rax` (for the 
above) and it'll show you the value of rax in decimal form._

## Sizes of Registers:

As seen above in the table, there are different names for the same registers 
depending on their size. `RAX` for example is a 64 bit register. `EAX` is the same
register, but only the lower 32 bits of RAX. And so on for `AX` and `AL` and `AH`.

The reason these registers subdivide into smaller sizes is to maintain backwards
compatibility. In the early days of computing, there weren't CPUs with 64 bit registers.
They had 8 bit CPUs, or 16 bit CPUs. Rather than redoing thousands of lines of code
and breaking compatibility for older devices that are still in use, larger bit registers
were built ontop of the smaller registers.

As for the sizes themselves, we can visualize `EAX` as being the lower half of `RAX`
and `AX` being the lower half of `EAX`. What is unique is that `AX` subdivides into
`AL` **and** `AH` (A lower, A Higher) - we can use both the lower 8 bits and upper 8
bits.

This naming conventions apply to a lot of the registers listed above in the table. 

<img src=https://diveintosystems.org/book/C7-x86_64/_images/register.png width=500>

### Reserved Registers

Some registers are automatically used for certain operations. One example is the `mul`
(multiplication) instruction.

```asm
mov eax, 5; copies 5 into eax register
mul 10; multiplies eax by 10
; answer is stored in edx:eax
```

This means, to multiply two numbers, one number must be inside the eax register. After
this instruction, the product is placed into edx:eax (lower 32 bits in eax, and if
needed, the upper 32 in edx).

Similarly, the `div` (division) instruction also is locked to the rax and rdx registers.

```asm
xor edx, edx ; clear the dividend
mov eax, 500 ; set the dividend
div 10 ; divides eax by 10
; answer is stored in eax, remainder stored in edx
```


### Argument Registers

When calling functions in Assembly from C/C++, the arguments you pass are stored into
very specific registers. These can vary from operating system to operating system.

In Linux at least, the order for the argument registers are as follows:

- `rdi`
- `rsi`
- `rdx`
- `rcx`
- `r8`
- `r9`
- Everything following these are stored on the stack

## SSE Registers

Surprise! There are more registers to get familiar with as you get deeper into x86 Assembly
When doing SSE Instructions (useful for performing calculations with floating point numbers),
you will end up using the xmm registers. Fortunately, these are much simpler in naming.

- `xmm0` , `ymm0` , `zmm0`
- `xmm1` , `ymm1` , `zmm1`
- `xmm2` , `ymm2` , `zmm2`
- `xmm3` , `ymm3` , `zmm3`
- `xmm4` , `ymm4` , `zmm4`
- `xmm5` , `ymm5` , `zmm5`
- `xmm6` , `ymm6` , `zmm6`
- `xmm7` , `ymm7` , `zmm7`

Unlike the regular registers which have a maximum size of 64 bits, these registers are 128 
bits in size. the `xmm0` - `xmm7` registers aren't even the biggest SSE registers you can have.

The `ymm0` - `ymm7` registers are 256 bits in size, with `xmm0` being the lower 128 bits of
the `ymm0` register. Don't get me started on `zmm0` with it's whopping 512 bits.

_Don't worry about SSE just yet, we'll cover that by itself later._

**In Conclusion** there are a lot of registers. 

----

# [Go back to the home page](HomePage.md)