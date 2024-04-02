---
{"dg-publish":true,"permalink":"/zh///dnode/"}
---


【C】{ASF, DF, FF, ZF, ONF}

```C
// 创建一个结点
dnode* DnodeAppend(dnode* any, void* addr, size_t typlen);
// [Unordered] [Alloc] Faster than `DnodeAppend()`
// <direction> `-2`from the head; `-1`left; `1`right; '2' from the tail 
dnode* DnodeInsert(dnode* nod, void* addr, size_t typlen, int direction);
// [Unordered]
dnode* DnodeBind(dnode* left, dnode* nod, dnode* right);
// [Ordered]
dnode* DnodeSort(dnode* any);
// [Unordered]
dnode* DnodeRewind(const dnode* any);
// [Unordered]
size_t DnodeCount(const dnode* any);
// [Unordered] [FailFlag:FoundNot/OptionNonexist]
// <direction> `-2`from the head; `-1`left; `1`right; '2' from the tail 
dnode* DnodeIndex(const dnode* any, void* addr, stdint* ref_span, int direction);
// [Unordered] [Alloc]
void DnodeRemove(dnode* some);
// [Unordered] [Alloc] in the direction of right.
void DnodeRelease(dnode* first);


```

【C++】

```C++
	class DnodeChain {
	public:
		DnodeChain(bool need_free);
		~DnodeChain();
		void Append(const void* addr, stduint typ);
		void Index(void* content);
		stduint Count() { return node_count; }
		Dnode* Root() { return root_node; }
		Dnode* Last() { return last_node; }
		void Remove(const stduint iden);
		Dnode* Remove(Dnode* content, bool systematic = true);
		void SetFreeContent(bool need_free);
		void Onfree(void(*fn_free)(void*) = 0, bool need_free = true, bool pass_whole = true) {
			_node_freefunc = fn_free;
			need_free_content = need_free;
			free_pass_whole = pass_whole;
		}
		void Sort();
		void Onsort(bool sorted = true, bool little_to_big = true, int (*fn_compare)(const void*, const void*) = 0) {
            this->sorted = sorted;
            this->little_endian = little_to_big;
            this->_node_compare = fn_compare;
        }
	protected:
		stduint node_count;
		Dnode* root_node;
		Dnode* last_node;
		bool need_free_content;
		//{TODO} below
		void(*_node_freefunc)(void*);
		bool sorted;
		bool little_endian;
		bool free_pass_whole;
		int (*_node_compare)(const void* addr0, const void* addr1);// return 0 for equal, 1 for greater, -1 for less
	};
```
