# Stage 1: Analysis

## Goal: Review the various Unix base-s, to see which are most
- secure
- portable
- Unix compliant
- POSIX compliant
- decoupled
- Actually necessary

find the "least bloated" variants of things like 

util-linux, coreutils, etc... and - 
pull binaries missing from the minimal sets into separate packages that can be added as needed/wanted/desired

After that:
compatibility shims/layers - if necessary... 
decoupling libraries/binaries

Next goals: 
Setting paths back where they belong `outside of /usr`

All "base tools" atleast should always be compiled statically
