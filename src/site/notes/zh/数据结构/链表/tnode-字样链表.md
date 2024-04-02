---
{"dg-publish":true,"permalink":"/zh///tnode/"}
---


【C】

```C
typedef struct TokenNode
{
    // {dnode} 
    struct TokenNode* next;
    char* addr;
    struct TokenNode* left;
    union { size_t len; toktype type; };
    size_t row, col;
} tode, tnode;// recommand using tnode. measures pointer[6]

#define _TNODE_COMMENT '#'
#define _TNODE_DIRECTIVE '%'
//
tnode* StrTokenAppend(tnode* any, const char* content, size_t contlen, size_t ttype, size_t row, size_t col);
// ...
#define TnodeLoad StrTokenAll
tnode* StrTokenAll(int (*getnext)(void), void (*seekback)(ptrdiff_t chars), char* buffer);
// {TODO} Merged into StrTokenReleases
void StrTokenClearAll(tnode* tstr);

// Free for self and its addr.
void TnodeReleaseTofreeDefault(void* inp);
// freefunc should memf the parameter-pointed object besides its resources.
void TnodesReleases(tnode* nod, void(*freefunc)(void*));
//
void StrTokenThrow(tnode* one);// a b c --> a c
//
inline static tnode* StrTokenBind(tnode* left, tnode* mid, tnode* right)
{
    if (left) left->next = mid;
    if (mid) mid->next = right;
    if (right) right->left = mid;
    if (mid) mid->left = left;
    return mid;
}
#define StrTokenPrint(first)\
    printf("Token: [R %llu,C %llu][%s] %s\n", first->row, first->col,\
        ((const char* []){"END", "ANY", "STR", "CMT", "DIR", "NUM", "SYM", "IDN", "SPC", "ELS"})\
        [first->type], first->type == tok_space ? "" : first->addr);

// For the string of the Tode.
#define StrTokenPrintAll(first)\
    do StrTokenPrint(first);\
    while (first = first->next);



```

【C++】

```C++
	class Tnode : public Dnode {
	public:
		Tnode*& left; // = (Tnode*&)(Dnode::left);
		Tnode*& next; // = (Tnode*&)(Dnode::next);
		stduint col, row;
		char*& addr; // = (char*&)Dnode::offs;
		Tnode(void* in_addr = 0, stduint typ = 0, Tnode* lef = 0, Tnode* nex = 0, \
			stduint col = 0, stduint row = 0) : col(col), row(row), addr((char*&)Dnode::offs), left((Tnode*&)Dnode::left), next((Tnode*&)Dnode::next){
			this->offs = in_addr;
			this->type = typ;
			this->left = lef;
			this->next = nex;
		}
		void Suspend(void (*freefunc)(Tnode*) = 0, Tnode** as_root = 0, \
			Tnode** as_last = 0, stduint** counts = 0);
	private:
		Dnode* dn;
	};

	class TnodeChain : public DnodeChain {
	public:
		TnodeChain(bool need_free = false);
		~TnodeChain();
		Tnode* Append(const void* addr, stduint contlen, stduint typ, stduint row, stduint col);
		void Sort();
		void Index(void* content);
		// stduint Count() ...
		Tnode* Root() {
			return (Tnode*)root_node;
		}
		Tnode* Last() {
			return (Tnode*)last_node;
		}
		
		void Remove(const stduint iden);
		void Remove(const void* content);
		Tnode* Remove(Tnode* nod, bool systematic = true);

		void SetFreeContent(bool need_free);
	protected:
		Tnode*& root_node; // = (Tnode*&)DnodeChain::root_node;
		Tnode*& last_node; // = (Tnode*&)DnodeChain::last_node;
		//{TODO}
	};

	class TokenParseUnit {
	private:
		TnodeChain* chain;
		int (*getnext)(void);
		void (*seekback)(stdint chars);
	public:
		stduint crtline;
		stduint crtcol;
		char* buffer, * bufptr;
		TokenParseUnit(int (*getnext)(void), void (*seekback)(stdint chars), char* buffer);
		~TokenParseUnit();
		TnodeChain* TokenParse();
		int Getnext() {
			crtcol++;
			return getnext();
		}
		void Seekpos(stdint chars) {
			seekback(chars);
		}
		TnodeChain* GetChain() {
			return chain;
		}
	};
```
