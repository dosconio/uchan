---
{"dg-publish":true,"permalink":"/zh///node/"}
---


【C】{ASF, DF, FF, ZF, ONF}

```C
// 创建一个结点
node* NodeAppend(node* first, void* addr);
// 插入一个结点
node* NodeInsert(node* first, void* addr);
// 对链表切换 Order 的时候重排 Node
node* NodeSort(node* first);
// 在链表中搜寻对应的内容最早的出现
size_t NodeIndex(const node* first, void* addr);
// 获取链表中结点的数量
size_t NodeCount(const node* first);
// 释放单个结点
void NodeRemove(node* nod, node* left);
// 释放链表资源
void NodeRelease(node* first);


```

【C++】

```C++
	class NodeChain {
	public:
		NodeChain(bool need_free);
		~NodeChain();
		Node* Append(const void* addr);
		toheap Node* Append(const char* addr);
		Node* Append(const void* addr, bool onleft, Node* nod = 0);
		void Index(void* content);
		stduint Count() { return node_count; }
		Node* Root() { return root_node; }
		Node* Last() { return last_node; }
		void Remove(const stduint iden);
		void Remove(const void* content);
		void Remove(Node* nod);
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
		Node* root_node;
		Node* last_node;
		bool need_free_content;
		void(*_node_freefunc)(void*);
		bool sorted;
		bool little_endian;
		bool free_pass_whole;
		int (*_node_compare)(const void* addr0, const void* addr1);// return 0 for equal, 1 for greater, -1 for less
	};

	template <typename type0> class LinearChain {
	public:
		stduint Count();
		type0*& Getval(stduint idx);
	private:
		// ...
	};
```
