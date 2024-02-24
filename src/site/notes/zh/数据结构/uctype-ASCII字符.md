---
{"dg-publish":true,"permalink":"/zh//uctype-ascii/"}
---


 【C】

```C
#define ascii_isdigit(c) ((c)-'0'<10)

#define ascii_islower(c) ((c)-'a'<26)

#define ascii_isupper(c) ((c)-'A'<26)

#define ascii_isalpha(c) ((c)-'A'<26||(c)-'a'<26)

#define ascii_isalnum(c) ((c)-'0'<10||(c)-'A'<26||(c)-'a'<26)

#define ascii_iscontrol(c) ((c)<32||(c)==127)

#define ascii_isprint(c) ((c)>=' '&&(c)<127)

#define ascii_isgraph(c) ((c)>' '&&(c)<127)

#define ascii_ispunct(c) ((c)!=' '&&(c)!='\t'&&(c)!='\n'&&(c)!='\r'&&(c)!='\v'&&(c)!='\f'&&(c)>='!'&&(c)<='~')

#define ascii_isspace(c) ((c)==' '||(c)=='\t'||(c)=='\n'||(c)=='\r'||(c)=='\v'||(c)=='\f')

#define ascii_isblank(c) ((c)==' '||(c)=='\t')

#define ascii_isxdigit(c) ((c)-'0'<10||(c)-'A'<6||(c)-'a'<6)

#define ascii_tolower(c) (_tab_tolower[c]) 

#define ascii_toupper(c) (_tab_toupper[c]) 

#define ascii_tohexad(c) ((c)>='a'?(c)-'a'+10:(c)>='A'?(c)-'A'+10 :(c)-'0')

```
