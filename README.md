﻿# Overheadless-obfuscication

The Intel x86 instruction set has been to be rather weird. It is an incredibly complex monster that underpins modern desktop computing. 
Besides it being, to just put it, frankly odd. It is also a really interesting source of easy questions that keep you busy for a long time.
In this blog series I will guide you through the journy that I have taken the past several years and highlight some of favorite places in this abyss of madness.

My journy started with a slighlty younger me with having the simple question "how many x86 instructions are there?". 
If we take C standerd library and we want to ask "How many functions does this library provide", we can probably get a decent answer pretty quickly. 
You can go to standard and count the defined functions there, take a look at it's source files, or maybe even some software tool just dumps it out for you with a simple command.

But to start answering this question I first needed to know what even an instruction is, where is defined, *how* is it defined? Can we easily find a list and what could we possibily do with it.

In this post we shall first explore what even an instruction is, how it is defined, and what does it do? 

Most desktops run on a intel or amd x86 CPU. These CPU's are large fat pieces of electronics that take a sequence of electronic input, and alter the state of it self, or something attached to it.
To make sense of the many things a CPU can execute we structed all the possible options it can perform into an *Instruction Set Architecture* or ISA for short. You can think of for example the instruction ```add``` that will take a number and increment some register somewhere in your computer.
So we talk about an x86 CPU, we mean that we are talking about a cpu that implements the x86 ISA.
You have a few flavors of ISA's, but we will ignore them because they are simply to different for what we are going to do.

Oddly enough there are 2 different ways to look at instructions, and you probably have seen them both in a limited fashion.
The first way is best given by example. ```ADD rax, 0x02 ```is an instruction, but so is ```MUL rbx, 0x40```, and ```MOV rax, rbx ``` too.
They all follow structure of ```name argument1, argument2```. Obviously there are slight variations on this like an instruction taking only 1 or no arguments, or special kind of arguments.
But they all follow this easy to comphrehand structure.

However how would a computer read this? Well they don't, they would read the binary encodings of this.
The creators of the ISA defined that when a CPU would read ```05 40``` that it would mean ```ADD``` 40 to the register called ```rax```.

Nearly everything your computer can read has an equivelant translation into the former form. The first form often also is called assembly and albeit rare, is still programmed in today to access special cpu features that is not exposed for example C. 
For example the C standard library doesn't state anything about virtualization so you need to resort to program in assembly or binary.

Internally all these instructions are translated into something called microcode, but how this actually works is kept secret (although you can still find some information). 

