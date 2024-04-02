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

【C++】

```C++
class Inode : public Node {
	public:
		Inode(const char* in_addr = 0, const void* data = 0, stduint typ = 0, bool readonly = false, bool typekeep = false) :  data(data), type(typ), readonly(readonly), typekeep(typekeep), next(0), addr((char*&)Node::offs) { addr = (char*)in_addr; }
		const void* data;
		stduint type;
		struct {
			bool readonly;
			bool typekeep;
		};
		Inode* next;
		// `char*& addr = (char*&)Node::offs;` MSVC default initializer can deal with this but GCC.
		char*& addr;
	};

	class InodeChain : public NodeChain {
	public:
		InodeChain(bool need_free = true);
		~InodeChain();
		void Append(const char* addr, const void* data, stduint typ, bool readonly = false, bool typekeep = false);
		void Sort();
		Inode* Index(const char* content);
		// inherited stduint Count() ... 
		Inode* Root() {
			return (Inode*)root_node;
		}
		Inode* Remove(Inode* inod, bool systematic = true);
		void Remove(const char* content);
		void SetFreeContent(bool need_free);
		bool Update(const char* iden, void* data, size_t typ, bool readonly = false, bool typekeep = false);
	protected:
		Inode*& root_node; // = (Inode*&)NodeChain::root_node;
		Inode*& last_node; // = (Inode*&)NodeChain::last_node;
		//{TODO}
	};
```
