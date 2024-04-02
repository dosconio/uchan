---
{"dg-publish":true,"permalink":"/zh//coear/"}
---


【C】{暂不查表故慢但精确}

```C
//LSB[SignFlap 0:N 1:Y]
coe* CoeTaylor(coe* dest, unsigned char dptor, const coe* period, size_t digcut);
//
int CoeIsNAN(const coe* co);
//
int CoeIsINF(const coe* co);
// Initial and set the necessary system structure.
void CoeInit();
// Reset the length of the digits. If the real precise is less, zero will be moved at the end of coff from expo; if more, will cut.
// param:direction 1:+inf 2:nearest 3:-inf 4:out
void CoeDig(coe* obj, size_t digits, int direction);
// Cut trailing zeros of coff and append to expo. This is usually used at the end of the operation, so some adaptation is done here. 
coe* CoeCtz(coe* dest);
//
coe* CoeDivrAlign(coe* o1, coe* o2);
//
coe* CoeDivrUnit(coe* obj, size_t kept_precise);
//
int CoeExpoAlign(coe* o1, coe* o2);
//
coe* CoeNew(const char* coff, const char* expo, const char* divr);
//
void CoeDel(coe* elm);
//
coe* CoeCpy(const coe* obj);
// Coe Version Of StrReheapStr
coe* CoeRst(coe* dest, char* coff, char* expo, char* divr);
// 取反。
coe* CoeNeg(coe* dest);
// 加法。
coe* CoeAdd(coe* dest, const coe* sors);
// 减法。
coe* CoeSub(coe* dest, const coe* sors);
// 比较。
int CoeCmp(const coe* o1, const coe* o2);
// 乘法。
coe* CoeMul(coe* dest, const coe* sors);
// 平方。
coe* CoeSquare(coe* dest);
// 绝对值。
coe* CoeHypot(coe* dest, const coe* sors);
// 除法。
coe* CoeDiv(coe* dest, const coe* sors);
// 取整数部分。
// CoeRem: make dest < unit_period
// Clear the mantissa part. Based on CoeExpoAlign().
coe* CoeInt(coe* dest);
// 幂。
coe* CoePow(coe* dest, const coe* sors);
// 带符号平方根。 Return a negative if dest is negative, otherwise a positive.
coe* CoeSqrt(coe* dest);
// 立方根。
// CoeCbrt
// 正弦。
coe* CoeSin(coe* dest);
// 余弦。
coe* CoeCos(coe* dest);
// 正切。
coe* CoeTan(coe* dest);
// 正弦反函数。
coe* CoeAsin(coe* dest);
// 余弦反函数。
coe* CoeAcos(coe* dest);
// 正切反函数。
coe* CoeAtan(coe* dest);
// Log`10(x) == Log`(default e)(x)/Log`e(10)
coe* CoeLog(coe* dest);
// 取符号。
int CoeSgn(const coe* dest);
// 自然幂。
coe* CoeExp(coe* dest);//TEST-STAGE
// 整数阶乘。
coe* CoeFac(coe* dest);
// 动态 圆周率常数。
coe* CoePi();
// 动态 自然常数。
coe* CoeE();
// 双曲正弦函数。
coe* CoeSinh(coe* dest);
// 双曲余弦函数。
coe* CoeCosh(coe* dest);
// 双曲正切函数。
coe* CoeTanh(coe* dest);
// 双曲正弦反函数。
coe* CoeAsinh(coe* dest);
// 双曲余弦反函数。
coe* CoeAcosh(coe* dest);
// 双曲正切反函数。
coe* CoeAtanh(coe* dest);
// coe 转 字符串。
// opt: 0[auto] 1[int or float] 2[e format]
char* CoeToLocale(const coe* obj, int opt);
// 字符串转 coe。
coe* CoeFromLocale(const char* str);
// coe 转 double。
double CoeToDouble(const coe* dest);
// 有符号整型转 coe。
coe* CoeFromInteger(ptrdiff_t integ);
// double 型转 coe。
coe* CoeFromDouble(double flt);


```

【C++】

```C++
namespace uni {
	class Coe /*: public coe*/ {
	public:
		Coe(const char* coff, const char* divr, const char* expo = "+0", stduint dimension = 0);
		Coe(double num);
		Coe(const char* local_str);
		Coe(const Coe& c);
		Coe(coe* c);
		~Coe();
		bool isnan();
		bool isinf();
		double GetReal() const;

		static Coe pi();
		static Coe e();

		String ToString(int opt = 0) const;
		operator double() const;
		operator String() const;

		//// 运算符的定义

		//{TEMP} no using: Coe res(CoeCpy(this->co)); CoeSin(res.co);
		Coe Sin()   { return Coe(sin  (operator double())); }
		Coe Cos()   { return Coe(cos  (operator double())); }
		Coe Tan()   { return Coe(tan  (operator double())); }
		Coe ASin()  { return Coe(asin (operator double())); }
		Coe ACos()  { return Coe(acos (operator double())); }
		Coe ATan()  { return Coe(atan (operator double())); }
		Coe Sinh()  { return Coe(sinh (operator double())); }
		Coe Cosh()  { return Coe(cosh (operator double())); }
		Coe Tanh()  { return Coe(tanh (operator double())); }
		Coe ASinh() { return Coe(asinh(operator double())); }
		Coe ACosh() { return Coe(acosh(operator double())); }
		Coe ATanh() { return Coe(atanh(operator double())); }
	// ...
	};
	
	extern const Coe coe_pi;
	extern const Coe coe_e;

}
```


