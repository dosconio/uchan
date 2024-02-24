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


