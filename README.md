Versor 2.0 is a C++11 Library that generates optimized geometric algebra code at compile-time.
It can handle arbitrary metrics and dimensions (limited by your compiler...).
                        
	git clone git://github.com/wolftype/vsr2.0.git
	cd vsr2.0
	git submodule init
	git submodule update

To test a graphics example

	make tests/xBasics.cpp
	
If you have errors see important makefile notes below

You need clang 3.2 or above or gcc 4.6 or above.  NOT tested on windows. 
If you don't want to or can't compile C++11 code try an older flavor of vsr
(github.com/wolftype/vsr.git) 

Homepage at versor.mat.ucsb.edu
                                                                      
To build with the 5D Conformal Model

	#include "vsr_cga3D.h"

To draw to screen

	#include "vsr_cga3D_draw.h"  

To inferface with elements using "G", "R", "S" keys to Grab, Rotate, or Scale:
                                   
	#include "vsr_cga3D_interface.h"
	
   
What's new? 

This compiles much faster than before, and without any silly predetermined list
of allowable operations or types.  Most notably, arbitrary metrics are now possible.  For example, 
the xRoots.cpp example calculates all the Euclidean 4D reflections of a couple of point groups
(F4 and D4, namely). So you can hypercube and polychoron away (8D cubes no problem!).  

As for CGA, all the Pnt, Vec, Dll notation remains as before, but i've started adding utility functions
since it helps people out. 

	auto pa = Point( 1,0,0 ); 
	auto pb = Point( 0,1,0 ); 
	auto pc = Point(-1,0,0 ); 
	auto c = Circle(pa, pb, pc); 
	
How does it work?

If you like mind-numbing functional template metaprogramming, take a look at the code
and let me know what you think.  If you don't, then I wouldn't . . .
	 

IMPORTANT NOTE ON MAKEFILE FLAGS

1. CLANG=path/to/clang/ (default usr/local/bin)
		The makefile assumes clang is at usr/local/bin/ -- if you want to change that set this flag  

2. GCC=1  (default 0)
		If you want to build with GCC set GCC=1.

3. RPI=1 (default 0)
        vsr also builds on the Raspberry Pi with a cross-compiler (GCC=1 RPI=1)
		(note you cannot build from the pi itself, you must use a cross-compiler)

3. GFX=0 (default 1) 
		if you want to build without graphics support you can set GFX=0
                                                                       