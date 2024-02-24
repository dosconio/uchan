---
{"dg-publish":true,"permalink":"/zh//datime/"}
---


【C】

```C
// 是否为闰年
#define isLeapYear(year) 
// 获取线性纪日标识
#define herspan(y,m,d)
// 获取周日起始的周的周编号
#define getHerWeekNumber(y,m,d) 
// 获取某天是星期几
unsigned weekday(word year, word month, word day);
// 获取某月有多少天
#define moondays(year, month)
// 将 tm 结构的时间转换为 POSIX 格式秒数
llong POSIXGetSeconds(struct tm* tm);
// Reverse function of herspan()
void fromherp(stdint herspans, word* year, word* month, word* day);


```


