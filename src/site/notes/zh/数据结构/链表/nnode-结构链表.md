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

【C++】

```C++
	class Nnode : public Tnode {
	// In fact is from Anode.h
	public:
		Nnode(void* addr = 0, Nnode* n_left = 0, Nnode* n_right = 0) :
			Tnode(addr, 0, (Tnode*)n_left, (Tnode*)n_right, 0, 0),
			addr((char*&)Dnode::offs), left((Nnode*&)Tnode::left), next((Nnode*&)Tnode::next) { subf = 0; bind = 0; }
		Nnode(Tnode* nod) : Tnode(*nod), addr((char*&)Dnode::offs), left((Nnode*&)Tnode::left), next((Nnode*&)Tnode::next) { subf = 0; data = 0; pare = 0; bind = 0; }
		Nnode*& left; // = (Nnode*&)Tnode::left;
		Nnode*& next; // = (Nnode*&)Tnode::next;
		char*& addr ; // = (char*&)Dnode::offs;
		Nnode* subf;
		Nnode* pare;// Want independent version? try Anode(anode.h)
		void* data;
		void* bind;
		//
		Nnode* Head() { // of parallel chain
			// return stepval(this->pare)->subf;// assert( while(...->left) )
			if (this->pare) return this->pare->subf; else {
				Nnode* crt = this; while (crt->left && (crt = crt->left));
				return crt;
			}
		}

		Nnode* Tail() { 
			Nnode* crt = this; while (crt->next && (crt = crt->next)); return crt;
		}

		bool isHead(Nnode* ifthen_reset = 0) {
			// simple: (this->pare) && (this->pare->subf == this)
			if (!this->pare) return (!this->left);
			if (this->pare->subf != this) return false;
			if (ifthen_reset) this->pare->subf = ifthen_reset;
			return true;
		}
		bool difline(Nnode* nod) { return this->row != nod->row; }
		Nnode* ReheapString(const char* str);
	};

	class NnodeChain : public TnodeChain {
	public:
		// INHERI: Count() ...
		NnodeChain(bool need_free);
		~NnodeChain();

		Nnode* Append(const void* addr, stduint typ, stduint col, stduint row);
		Nnode* Append(Tnode* tnode);// from outside of chain

		Nnode* Insert(Nnode* insnod, bool onleft = false, \
			const void* addr = 0, stduint typ = 0);
		Nnode* Insert(Nnode* insnod, Dnode* dnod, bool onleft = false);
		Nnode* Receive(Nnode* insnod, DnodeChain* dnod, bool onleft = false);

		void Sort();

		void Index(void* content);

		// can use by pseudo static (set this zero)
		Nnode* Adopt(Nnode* thisn, Nnode* subhead, Nnode* subtail = (Nnode*)~(stduint)0, bool go_func = true);

		Nnode* Root() { return (Nnode*)root_node; }
		Nnode*& RootAddress() { return root_node; }

		Nnode* Last() { return (Nnode*)last_node; }// of main trunk

		void Remove(const stduint iden);
		void Remove(const void* content);
		Nnode* Remove(Nnode* nod, bool systematic = true) {
			return NnodeRelease(nod, this, systematic);
		}

		void SetFreeContent(bool need_free);

		//[ASSUME] Contents Heaped
		NNODE_DIVSYM_RETYPE DivideSymbols(Nnode* inp, stduint width, stduint idx);
		
	protected:
		Nnode*& root_node; // = (Nnode*&)TnodeChain::root_node;
		Nnode*& last_node; // = (Nnode*&)TnodeChain::last_node;
		//{TODO}
		static Nnode* NnodeRelease(Nnode* nod, NnodeChain* nc, bool systematic = true);
		static void NnodesRelease(Nnode* nods, NnodeChain* nc);
	};

	class NestedParseUnit {
	private:
		NnodeChain* chain;
	public:
		bool parsed;
		/*tofree*/ char* msg_fail;
		stduint linemn_no, column_no;
		NodeChain* TokenOperatorGroupChain;
		NestedParseUnit(TnodeChain& tchain, NodeChain* TOGCChain);// will destructure TnodeChain
		~NestedParseUnit();
		NnodeChain* GetNetwork() { return chain; }
		// Process:
		bool Parse() {
			return NnodeParse(chain->Root(), chain);
		}
	protected:
		bool NnodeParse(Nnode* tnod, NnodeChain* chain, bool merge_parensd = true);
		bool ParseOperator(Nnode* pare, NnodeChain* nc);
	};

	typedef void(*_tok_bindfunc_t)(DnodeChain* io);
	
	struct TokenOperator {
		const char* idnop;
		const char* ident;
		_tok_bindfunc_t bindfn;
	};

	class TokenOperatorGroup {
	public:
		TokenOperator* operators;
		stduint count;
		bool left_to_right;
		stduint condition;// "?:" is ternary conditional operator
		//
		TokenOperatorGroup(TokenOperator* ops, stduint cnt, bool ltr = true, stduint cond = 2) {
			operators = ops; count = cnt; left_to_right = ltr; condition = cond;
		}
	};// usually arranged by levels for its array/chain
}

const char* StrIndexOperator(const char* str, uni::TokenOperator** operators, size_t count, bool left_to_right);


```
