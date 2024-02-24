---
{"dg-publish":true,"permalink":"/zh//ustring/"}
---


【C】【C++】

```C
//
#define StrCompareLocale strcoll
//
#define StrCopyLocale strxfrm
//
#define StrGetError strerror
//---- ---- ---- ---- { General String Function } ---- ---- ---- ----
// [ASTRING] Convert char in string in heap
// equivalent `StrHeapAppendChars("", c, 1)` ---> {TODO: auto omit null destination string}
char* StrHeapFromChar(char c);
// [ASTRING]
char* StrHeap(const char* valit_str);
// [ASTRING]
void* MemHeap(const void* sors, size_t bytelen);
// [ASTRING]
char* StrHeapN(const char* valit_str, size_t strlen);
// [ASTRING]
char* StrHeapAppend(const char* dest, const char* sors);
// [ASTRING]
char* StrHeapAppendN(const char* dest, const char* sors, size_t n);
// [ASTRING]
char* StrHeapAppendChars(char* dest, char chr, size_t n);
// [ASTRING]
char* StrReplace(const char* dest, const char* subfirstrom, const char* subto, size_t* times);
// [ASTRING]
char* StrHeapInsertThrow(const char* d, const char* s, size_t posi, size_t thrown);
// [ASTRING]
char* instoa(ptrdiff_t num);// [Instant to ASCII yo heap]
//
char* MemRelative(char* addr, size_t width, ptrdiff_t times)
//
char* MemAbsolute(char* dest, const char* sors, size_t width)
//
char* StrCopy(char* dest, const char* sors)
//
void* MemSet(void* s, int c, size_t n)
//
void* MemCopyN(void* dest, const void* sors, size_t n)
//
char* StrCopyN(char* dest, const char* sors, size_t n)
//
char* StrAppend(char* dest, const char* sors)
//
char* StrAppendN(char* dest, const char* sors, size_t n)
///
char* StrAppendChars(char* dest, char chr, size_t n)
//---- ---- ---- ---- { Compare Function } ---- ---- ---- ----
//
int MemCompare(const char* a, const char* b, size_t n)
//
int StrCompare(const char* a, const char* b)
///{TODO} 2 Ver
int StrCompareInsensitive(const char* a, const char* b)// RFC12
//
int StrCompareN(const char* a, const char* b, size_t n)
///{TODO} 2 Ver
int StrCompareNInsensitive(const char* a, const char* b, size_t n)// RFC12
// 
size_t StrLength(const char* s)
//{TODO} 2 Ver
char* StrElement(char* s, ptrdiff_t idx)
//{TODO} 2 Ver
char StrCharLast(const char* s)//= *StrElement(s, -1)
//
const char* MemIndexByte(const char* s, int c, size_t n)
//
const char* StrIndexChar(const char* s, int c)
//
const char* StrIndexCharRight(const char* s, int c)
//
size_t StrLengthSameChar(const char* str, int c, const char** ret)
//
const char* StrIndexString(const char* dest, const char* sub)
//
size_t StrSpanInclude(const char* s1, const char* s2)
//
size_t StrSpanExclude(const char* s, const char* reject)
//
const char* StrIndexChars(const char* s1, const char* s2)
//{TODO} 2 Ver
const char* StrIndexCharsExcept(const char* s1, const char* s2)// RFV24
//{TODO} 2 Ver
const char* StrIndexCharsRight(const char* s1, const char* s2)// RFV19
//
//{TODO} const char* StrIndexCharsExceptRight(const char* s1, const char* s2)
//
void StrFilterOut(char* p, char c);
//TODO. no considering new-line
void StrFilter(char* p, toktype tt);
//
void StrFilterString(char* p, const char* needs);
//
void StrFilterOutString(char* p, const char* neednot);
//
size_t StrDeprefixSpaces(char* str);
//
size_t StrDesuffixSpaces(char* str);
//
char* StrTokenOnce(char* s1, const char* s2)

//---- ---- ---- ---- { Set and Sorting } ---- ---- ---- ----

// 
void StrSortBubble(char* str, int order);
// 
char* StrToLower(char* str)
// 
char* StrToUpper(char* str)
//{TODO} StrRelative and StrRelativeN
#define StrSubWithdraw(posi_start,len)\
    MemRelative((posi_start), StrLength(posi_start) + 1, -(ptrdiff_t)(len))
//
char* instob(ptrdiff_t num, char* buf);
//
ptrdiff_t atoins(const char* str);
//---- ---- ---- ---- { ChrAr } ---- ---- ---- ----
// Clear prefix zeros, "+001"-->"+1".
size_t ChrCpz(char* str);
// Char-Arithmetic Cut Trailing zeros. Return the counts of chars that have been cut.
size_t ChrCtz(char* str);
//
char* _Need_free ChrHexToDec(const char* hex);
// Output: upper case
char* ChrDecToHex(char* dec);
//
char* _Need_free ChrHexToDecFloat(const char* hexf);
//
char* _Need_free ChrDecToHexFloat(const char* decf, size_t digits);
// 加法。
char* ChrAdd(const char* dest, const char* sors);
// 减法。
char* ChrSub(const char* dest, const char* sors);
// 乘法。
char* ChrMul(const char* a, const char* b);
// 除法。返回项目 “a”作为商，“b”作为余数。
void ChrDiv(char* a, char* b);
// 阶乘。“a” 有前缀 '+'。
char* ChrFactorial(const char* a);
// 全排列。
char* ChrArrange(const char* total, const char* items);
// 全组合。
char* ChrCombinate(const char* total, const char* items);
// 最大公因数。
char* ChrComDiv(const char* op1, const char* op2);
// 最小公倍数。
char* ChrComMul(const char* op1, const char* op2);
//
char* ChrInsPow(const char* in, size_t times);
//---- ---- ---- ---- { ChrAr General } ---- ---- ---- ----
//
int ChrCmp(const char* a, const char* b);// -1 0 1
//
void DigInc(int ascii, char* posi);
//
void DigDec(int ascii, char* posi);
//---- ---- ---- ---- { Others or Temporarily Stage Area } ---- ---- ---- ----
// 9876.5432H <=== 0x32,0x54`0x76,0x98;
char* _Need_free bcdtoa(unsigned char* str, size_t bylen);
// 98765432H ===> 0x32,0x54,0x76,0x98;
unsigned char* _Need_free atobcd(char* str);
// Boundary
unsigned char StrShiftLeft4(void* s, size_t len);
// Boundary
void StrShiftLeft8n(void* s, size_t len, size_t n);
// Boundary
unsigned char StrShiftRight4(void* s, size_t len);
// Boundary, may renamed StrShiftRightBytes
void StrShiftRight8n(void* s, size_t len, size_t n);
// In the direction of the left
stdint MemCompareRight(const unsigned char* a, const unsigned char* b, size_t n);


```


