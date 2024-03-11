---
{"dg-publish":true,"permalink":"/zh//stack/"}
---


【C】

```C
#define push(x) stack_push(0, &(x), sizeof(x))
#define pop(x) stack_pop(0, (void*)&(x), sizeof(x))

// Return 0 if success, else return -1

int stack_init(struct stack_t* stack, size_t size);

int stack_push(struct stack_t* stack, const void* data, size_t size);

int stack_pop(struct stack_t* stack, void* data, size_t size);

void stack_free(struct stack_t* stack);

void stack_global_event_full(void (*if_full)(void));

```

【C++】

```C++
template <typename type0> class Stack {
public:
	Stack(unsigned size);
	~Stack();
	void push(type0 item);
	type0 pop();
	bool isEmpty();
	bool isFull();
private:
	unsigned size;// todo size_t
	unsigned ptr;// todo size_t
	type0* stack;
};
```
