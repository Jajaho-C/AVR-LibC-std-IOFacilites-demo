# AVR-LibC-std-IOFacilites-demo
AVR-LibC demo project for the standard io facilities of the library.  
Source: https://www.nongnu.org/avr-libc/user-manual/group__stdiodemo.html  

Contains uart.c and uart.h.  

Contains these useful macros that enable symbolic programming.
``` C
#define GLUE(a, b)  a##b

/* single-bit macros, used for control bits */
#define SET_(what, p, m) GLUE(what, p) |= (1 << (m))
#define CLR_(what, p, m) GLUE(what, p) &= ~(1 << (m))
#define GET_(/* PIN, */ p, m) GLUE(PIN, p) & (1 << (m))
#define SET(what, x) SET_(what, x)
#define CLR(what, x) CLR_(what, x)
#define GET(/* PIN, */ x) GET_(x)

/* nibble macros, used for data path */
#define ASSIGN_(what, p, m, v) GLUE(what, p) = (GLUE(what, p) & \
						~((1 << (m)) | (1 << ((m) + 1)) | \
						  (1 << ((m) + 2)) | (1 << ((m) + 3)))) | \
					        ((v) << (m))
#define READ_(what, p, m) (GLUE(what, p) & ((1 << (m)) | (1 << ((m) + 1)) | \
					    (1 << ((m) + 2)) | (1 << ((m) + 3)))) >> (m)
#define ASSIGN(what, x, v) ASSIGN_(what, x, v)
#define READ(what, x) READ_(what, x)
```
