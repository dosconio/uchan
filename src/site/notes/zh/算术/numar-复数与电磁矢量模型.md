---
{"dg-publish":true,"permalink":"/zh//numar/"}
---


【C】

```C
//
#define NumInit() CoeInit()
//
dima* NumNewComplex(const char* Rcof, const char* Rexp, const char* Rdiv,
    const char* Icof, const char* Iexp, const char* Idiv);
//
dima* NumNew(const char* xcoff, const char* ycoff, const char* zcoff, const char* tcoff);
//
dima* NumCpy(const dima* num);
//
void NumDel(dima* num);

// ---- ---- ---- ---- Convert ---- ---- ---- ---- 
//
cplx_d NumToComplex(const dima* dest);
//
dima* NumFromComplex(cplx_d flt);
// opt: 0[auto] 1[int or float] 2[e format]
char* NumToString(const dima* dest, int opt);
// ---- ---- ---- ---- Operator ---- ---- ---- ---- 
// For complex and 4d-vector
coe* NumAbs(const dima* s);
// Return zoyo (-pi,pi]
coe* NumAng(const dima* s);
// For complex and 4d-vector
void NumAdd(dima* dest, const dima* sors);
// For complex and 4d-vector
void NumSub(dima* dest, const dima* sors);
// For complex and 4d-vector(aka. NumDot)
void NumMul(dima* dest, const dima* sors);
// {TEMP}. Ultimate target zo for for D[xyz]+.
void NumCross(dima* dest, const dima* sors);
//
void NumDiv(dima* dest, const dima* sors);
//
void NumPow(dima* dest, const dima* sors);
//
void NumSqrt(dima* dest);
//
void NumExp(dima* dest);
//
void NumLog(dima* dest);// based on e
//
void NumSin(dima* dest);
//
void NumCos(dima* dest);
//
void NumTan(dima* dest);
//
void NumAsin(dima* dest);
//
void NumAcos(dima* dest);
//
void NumAtan(dima* dest);
//
void NumSinh(dima* dest);
//
void NumCosh(dima* dest);
//
void NumTanh(dima* dest);
//
void NumAsinh(dima* dest);
//
void NumAcosh(dima* dest);
//
void NumAtanh(dima* dest);


```


