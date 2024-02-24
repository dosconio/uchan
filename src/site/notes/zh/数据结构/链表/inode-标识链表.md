---
{"dg-publish":true,"permalink":"/zh///inode/"}
---


【C】

```C
typedef struct IdenNode
{
    struct IdenNode* right;
    char* addr;// for order
    //
    void* data;
    size_t type;
    size_t property;
} inode;

// No duplicate check. prop[2:Not-change-prevous]
inode* InodeUpdate(inode* inp, const char* iden, void* data, size_t typ, size_t prop, void(*freefunc_element)(void*));
// used name: InodeDelete ---> InodeRemove
void InodeDelete(inode* inp, const char* iden, void(*freefunc)(void*));
// InodeLocate ---> InodeIndex
inode* InodeLocate(inode* inp, const char* iden, inode** refleft);
// in the direction of right.
void InodesRelease(inode* first, void(*freefunc)(void*));


```


