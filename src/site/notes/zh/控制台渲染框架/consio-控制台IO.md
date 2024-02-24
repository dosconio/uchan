---
{"dg-publish":true,"permalink":"/zh//consio-io/"}
---


【C】

```C
// Return the length of the words excluding terminating zero but "limit" considers it.
size_t ConScanLine(char* buf, size_t limit);

#if defined(_Linux)
//
void ConCursorMoveUp(unsigned short dif)
//
void ConCursorMoveDown(unsigned short dif)
//
void ConCursorMoveRight(unsigned short dif)
//
void ConCursorMoveLeft(unsigned short dif)
//
void ConCursorReset(void)
//
void ConCursor(unsigned short col, unsigned short row)
//
static inline void ConCursorShow(void)
//
void ConClear(void);
//
static inline void ConCursorHide(void)

// The style is for the brush
void ConStyleAbnormal(void);
// The style is for the brush
void ConStyleNormal(void);
// ConCurrentWorkingDirectory
#ifdef _WinNT
    #include <direct.h>
    #define ConGetCurrentDirectory _getcwd
    #define ConSetCurrentDirectory _chdir// return 0 if success
#elif defined(_Linux)
    #include <unistd.h>
    #define ConGetCurrentDirectory getcwd
    #define ConSetCurrentDirectory chdir
#endif



```


