Topic:[[Programming]]
Link : [Optimization of code through SIMD](http://www.cs.uu.nl/docs/vakken/magr/2017-2018/files/SIMD%20Tutorial.pdf)
Single Instruction Multiple Data

## Key concepts
- Instruction level parallelism: the capabilty of the CPU to execute multiple instructions simultaneously, i.e., in the same cycle, in the a single thread.
- SIMD instructions can significantly increase the performane  when exactly the ==same operations== are to be performed on ==multiple data objects==, e.g., graphic processing and digital signal processing.
- SSE: Streaming SIMD Extensions.
- CPU uses registers to store data. ==C++ vectors== remain vectors even at the assembler level: rather than storing separate values in separate registers, we store vector values in a single vector register.(Depending on the size of the register! 32 bit can have char a[4] )
- 4 parallel instructions execution still waste ==50 %== of the compute potential on AVX machines. We need more jobs to attain maximum effiecieny.
- Reaching 100% efficiency requires that the input array is a ==multiple of 4 or 8==
- For data parallel algortihm, each of the scalars in a SIMD register hold the data for ==one thread==.
- int a;
- float &b = (float &)a;
- This creates one int and a float reference to that integer. we can so a similar thing with union{ int a ; float ;}; both a and b reside in the same memory location. 
- Basic types and sizes in C++: char 8 bit, short 16 bit, int and float 32 bit. 
- An SSE register is 128 bits in size, __m128(float call it 'quadfloat') and __m128i(for int and call it 'quadint'). Similarly, AVX has __m256(octfloat) and __m256i(octint). SSE and AVX have 16 registers each.
## Practical useage:
```C++
#include "nmintrin.h" // for SSE
#included "immintrin.h"//for AVX
union {__m128 a4; float a[4]}
//in this way we can access individual floats in __m128 directly. We can also create the quadfloat directly:
__m128 a4 = _mm_set_ps(4.0f,4.1f,4.2f,4.3f);
__m128 b4 = _mm_set_ps(1.0f,1.0f,1.0f,1.0f);
// To add them together we use _mm_add_ps:
__m128 sum4 = _m_add_ps( a4, b4);
// keywords like _mm_add_ps and _mm_set_ps are called intrinsics.
_mm_sub_ps(a4,b4);
_mm_mul_ps(a4,b4);
//For AVX we use similar intrinsics but just change the name of our variables to __m256 as it has 256 bits.
__m256 result
float * f=(float *) &result
//now you can access it as array.. f[i]
```
[The Intel Intrinsic Guide]()
