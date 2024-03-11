---
{"dg-publish":true,"permalink":"/zh//strpool/"}
---


【C】

```C
//
void StrPoolInit();
//
char* StrPoolHeap(const char*, size_t);
//
char* StrPoolAlloc(size_t);
//
char* StrPoolAllocZero(size_t);
//
void StrPoolRelease();

```

【C++】

```C++
	class Strpool {
	public:
		Strpool(stduint defablk = 0x1000);
		~Strpool();
		byte* Alloc(stduint size, const byte* mempos = 0);// make use of MemCopyN
		byte* AllocZero(stduint size);// initialize with 0
		byte* AllocString(const char* str, stduint length = 0);
	private:
		stduint unit_size;
		byte* root_pool;
		byte* last_pool;
		byte* crt_pool;
		stduint local_ptr;// < unit_size
		byte* new_pool(stduint len=0);// and switch to it
	};
```

