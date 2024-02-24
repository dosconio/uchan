---
{"dg-publish":true,"permalink":"/zh//crc64-crc-64/"}
---


【C】

```C
// 获取数据 CRC64 校验码
uint64_t HashCRC64Bytes(const byte* data, size_t length, uint64_t crc, uint64_t polynomial, uint64_t final_xor, int refl);
// 获取文件 CRC64 校验码
uint64_t HashCRC64File(FILE* fptr, uint64_t crc, uint64_t polynomial, uint64_t final_xor, int refl);
// 获取数据 CRC64 校验码的一次迭代
uint64_t HashCRC64Once(uint64_t last, byte data, uint64_t polynomial, int refl);
// 对一次迭代的结果进行最后的处理
uint64_t HashCRC64Endo(uint64_t last, uint64_t final_xor, int refl);


```


