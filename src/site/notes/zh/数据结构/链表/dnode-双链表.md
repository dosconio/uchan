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


