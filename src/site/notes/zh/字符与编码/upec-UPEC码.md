---
{"dg-publish":true,"permalink":"/zh//upec-upec/"}
---




【C】

```C
// 是否为白面字符
#define isuspace(c) (c <= 0x10 && c > 0x08)
// 是否为阿拉伯数字
#define isudigit(c) ((c & 0b11110000) == 0b00010000)
// 是否为大写的字母符号
#define isuupper(c) ((c & 0b11100000) == 0b00100000)
// 是否为小写的字母符号
#define isulower(c) ((c & 0b11100000) == 0b01100000)
// 是否有形字符
#define isupunct(c) ((c & 0b11100000) == 0b01000000)
// 转换为小写形式
#define toulower(c) (isuupper(c)? (c) | 0b01000000 : (c))
// 转换为大写形式
#define touupper(c) (isulower(c)? (c) & 0b10111111 : (c))
// UPEC 编码转换为 ASCII 字符
static char upec2ascii(char upec);
// ASCII 编码转 UPEC 编码
static char ascii2upec(char ascii);

```

