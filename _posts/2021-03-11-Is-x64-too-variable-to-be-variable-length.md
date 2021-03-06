---
layout: post
title:  "Is x64 too variable to be variable width?"
date:   2021-03-11 13:09:46 +0200
categories: x86 bin
---

In the design of Instruction Set Architectures, a common divide is drawn between fixed length and variable length.
For instance, all instructions in MIPS are represented by the same number of bytes. 
If we take the definition of variable length to not be fixed length, then we get some funny situations.

In x64 there are prefixes which get ignored but can be repeated an arbtirarly number of times. These are the segment override prefixes for CS DS ES and SS.
Thus if we take each instruction and encode it normally, but this time we would add any of these prefixes until we hit the maximum number of bytes in the x64 ISA which is defined to be 15, then we are able to represent all instructions with the same number of bytes.

If can represent all instructions with the same numbers of bytes, would it be a stretch to call it a fixed-length instruction set? 
