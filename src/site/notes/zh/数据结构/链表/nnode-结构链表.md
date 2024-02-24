---
{"dg-publish":true,"permalink":"/zh///nnode/"}
---


【C】

```C
typedef struct NestNode
{
    // { tode }
    struct NestNode* right;
    char* addr;
    struct NestNode* left;
    size_t type;// from `class` for C++ keyword compatibility
    size_t row, col;
    //
    struct NestNode* subf;// sub-first item
    union { void* bind; size_t flag; struct NestNode* pare; };
} nnode;// {comb with nnode}

// param:direction [0:L 1:R]#cancelled[2:SubHead 3:SubTail]
nnode* NnodeInsert(nnode* nod, int direction, nnode* parent);
// Set a part of nnode as the sub of a nnode. If subtail is null, this is for all the right part of the nnode string. If only one item, keep subhead and subtail same.
nnode* NnodeBlock(nnode* nod, nnode* subhead, nnode* subtail, nnode* parent);
// Free for self and its addr.
void NnodeReleaseTofreeDefault(void* inp);
// If freefunc is not null, free for memory will be defined by user, or just free the node block. In the direction of right.
void NnodeRelease(nnode* nod, nnode* parent, void(*freefunc)(void*));
// If freefunc is not null, free for memory will be defined by user, or just free the node block. In the direction of right.
void NnodesRelease(nnode* nod, nnode* parent, void(*freefunc)(void*));


```


