---
{"dg-publish":true,"permalink":"/zh//regar/"}
---


【C】

```C
//
size_t RsgDiv8(size_t* sstr, size_t slen, unsigned char divr);
//
signed RsgCmp(const size_t* a, const size_t* b, size_t alen, size_t blen);
//
int RsgMul8(size_t* sstr, size_t slen, unsigned char mult);
//
int RsgAdd8(size_t* sstr, size_t slen, unsigned char plus);
//
int RsgSub8(size_t* sstr, size_t slen, unsigned char subr);
//
size_t* _Need_free RsgResize(const size_t* sstr, size_t slen, size_t dlen);
//
char* _Need_free RsgToString(const size_t* sstr, size_t slen, signed syst);
//
int RsgAdd(size_t* dstr, const size_t* sstr, size_t comlen);
//
int RsgSub(size_t* dstr, const size_t* sstr, size_t comlen);
//
void RsgSubComple(size_t* dstr, const size_t* sstr, size_t comlen);
//
int _Heap RsgMul(size_t* dstr, const size_t* sstr, size_t comlen);
//
int _Heap_tmpher RsgDiv(size_t* dstr, size_t* sstr, size_t comlen);
//
size_t* _Need_free RsgNew(const size_t* sors, size_t len);
//
size_t* _Need_free RsgImm(size_t sors, size_t len);
//
int _Heap_tmpher RsgPow(size_t* base, const size_t* expo, size_t comlen);
//
int _Heap RsgArrange(size_t* total, const size_t* items, size_t comlen);
//
int _Heap RsgFactorial(size_t* base, size_t comlen);
//
int _Heap RsgCombinate(size_t* total, const size_t* items, size_t comlen);
//
int _Heap RsgComDiv(size_t* d, const size_t* s, size_t comlen);
//
int _Heap RsgComMul(size_t* d, const size_t* s, size_t comlen);
//
Rfnar_t* _Need_free RedNew(size_t* coff, size_t* expo, size_t* divr, size_t len);
//
Rfnar_t* _Need_free RedNewImm(size_t coff, size_t expo, size_t divr, size_t len);
// all _Heap:
void RedDel(Rfnar_t* elm);
//
Rfnar_t* RedHeap(const Rfnar_t* obj);
//
void RedDig(Rfnar_t* dest, size_t prec);
//
void RedZip(Rfnar_t* dest);
//
void RedAlignExpo(Rfnar_t* d, Rfnar_t* s);
//
void RedExpoZero(Rfnar_t* d);// RFV2 ArnMgk
//
void RedDivrUnit(Rfnar_t* d);
//
void RedReduct(Rfnar_t* d);
//
void RedAlign(Rfnar_t* d, Rfnar_t* s);
//
int RedAdd(Rfnar_t* d, const Rfnar_t* s);
//
int RedSub(Rfnar_t* d, const Rfnar_t* s);
//
int RedCmp(const Rfnar_t* d, const Rfnar_t* s);
//
int RedMul(Rfnar_t* dest, const Rfnar_t* sors);
//
int RedDiv(Rfnar_t* dest, const Rfnar_t* sors);
//
double _Heap RedToDouble(const Rfnar_t* dest);
//
Rfnar_t* _Need_free RedFromDouble(double flt, size_t rfnumlen, size_t FetchDigits);
Hrnar_t* HrnImm(size_t xcoff, size_t xexpo, size_t xdivr,\
    size_t ycoff, size_t yexpo, size_t ydivr,\
    size_t zcoff, size_t zexpo, size_t zdivr,\
    size_t tcoff, size_t texpo, size_t tdivr,\
    size_t comlen);
//
Hrnar_t* HrnCpy(const Hrnar_t* obj);
//
void HrnClr(Hrnar_t* d);
//
void HrnAdd(Hrnar_t* d, const Hrnar_t* s);
//
void HrnSub(Hrnar_t* d, const Hrnar_t* s);
//
Hrnar_t* HrnCross(const Hrnar_t* d, const Hrnar_t* s);
//
Rfnar_t* HrnDot(const Hrnar_t* d, const Hrnar_t* s);
//
Rfnar_t* _Need_free HrnAbs(const Hrnar_t* d);


```


