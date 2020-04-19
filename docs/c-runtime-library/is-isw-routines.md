---
title: is、isw 系ルーチン
ms.date: 11/04/2016
api_location:
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- isw
- is
helpviewer_keywords:
- is routines
- isw routines
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
ms.openlocfilehash: 4dad7ff74112da7fc7d0d01714b0cf0dd4e4495c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940172"
---
# <a name="is-isw-routines"></a>is、isw 系ルーチン

|||
|-|-|
|[isalnum、iswalnum、_isalnum_l、_iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph、iswgraph、_isgraph_l、_iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|
|[isalpha、iswalpha、_isalpha_l、_iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte、_isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|
|[isascii、__isascii、iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower、iswlower、_islower_l、_iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|
|[isblank、iswblank、_isblank_l、_iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint、iswprint、_isprint_l、_iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|
|[iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct、iswpunct、_ispunct_l、_iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|
|[iscsym、iscsymf、__iscsym、\__iswcsym、\__iscsymf、\__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|[isspace、iswspace、_isspace_l、_iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|
|[_isctype、iswctype、_isctype_l、_iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper、_isupper_l、iswupper、_iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|
|[isdigit、iswdigit、_isdigit_l、_iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|

## <a name="remarks"></a>解説

これらのルーチンは、文字が指定条件を満たしているかどうかをテストします。

**is`EOF` ルーチンは、-1 (** ) から **UCHAR_MAX** (0xFF) までの任意の整数の引数に対して意味のある結果を生成します。 `int` 型の引数が必要です。

> [!CAUTION]
> **is** ルーチンで `char` 型の引数を渡すと、予測できない結果が発生する可能性があります。 0x7F よりも大きい値を持つ `char` 型の SBCS または MBCS の 1 バイト文字は負になります。 `char` が渡されると、コンパイラはその値を符号付き `int` または符号付き **long** に変換することがあります。 この値は、コンパイラによって符号拡張されることがあり、予想外の結果になることがあります。

**isw** ルーチンは、-1 (**WEOF**) から 0xFFFF までの任意の整数値に対して意味のある結果を生成します。 **wint_t** データ型は、WCHAR.H で **unsigned short** として定義されており、任意のワイド文字またはワイド文字のファイル終端 (**WEOF**) 値を保持できます。

出力値は、ロケールの `LC_CTYPE` カテゴリの設定に影響されます。詳細については、「[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)」を参照してください。 **_l** サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のロケールを使用します。 **_l** サフィックスが付いているバージョンは、渡されたロケール パラメーターを代わりに使用する点を除いて同じです。

"C" ロケールでは、**is** ルーチンのテスト条件は次のようになります。

`isalnum`<br/>
英数字 (A - Z、a - z、または 0 - 9)。

`isalpha`<br/>
英字 (A - Z または a - z)。

`__isascii`<br/>
ASCII 文字 (0x00 - 0x7F)。

`isblank`<br/>
水平タブまたは空白文字 (0x09 または 0x20)。

`iscntrl`<br/>
制御文字 (0x00 - 0x1F または 0x7F)。

`__iscsym`<br/>
文字、アンダースコア、または数字。

`__iscsymf`<br/>
文字またはアンダースコア。

`isdigit`<br/>
10 進数 (0 - 9)。

`isgraph`<br/>
空白 ( ) を除く印刷できる文字。

`islower`<br/>
小文字 (a - z)。

`isprint`<br/>
空白を含む印刷できる文字 (0x20 - 0x7E)。

`ispunct`<br/>
区切り記号。

`isspace`<br/>
空白文字 (0x09 - 0x0D または 0x20)。

`isupper`<br/>
大文字 (A - Z)。

`isxdigit`<br/>
16 進数字 (A - F、a - f、または 0 - 9)。

**isw** ルーチンでは、指定条件に基づくテストの結果は、ロケールに依存しません。 **isw** 関数のテスト条件は次のとおりです。

`iswalnum`<br/>
`iswalpha` または `iswdigit`。

`iswalpha`<br/>
`iswcntrl`、`iswdigit`、`iswpunct`、または `iswspace` がいずれも 0 になる実装定義セットに含まれる任意のワイド文字。 `iswalpha` は、`iswupper` または `iswlower` が 0 以外の値になるワイド文字に対してのみ、0 以外の値を返します。

`iswascii`<br/>
ASCII 文字のワイド文字表現 (0x0000 - 0x007F)。

`iswblank`<br/>
標準の空白文字に対応するワイド文字、または `iswalnum` が false になるワイド文字の実装定義セットに含まれるワイド文字。 標準の空白文字は空白 (L' ') と水平タブ (L'\t') です。

`iswcntrl`<br/>
制御ワイド文字。

`__iswcsym`<br/>
`isalnum` が true である任意のワイド文字または '_' 文字。

`__iswcsymf`<br/>
`iswalpha` が true である任意のワイド文字または '_' 文字。

`iswctype`<br/>
文字には、`desc` 引数で指定されたプロパティがあります。 `desc` の `iswctype` 引数の有効な値には、次の表に示すようにそれぞれ同等のワイド文字分類ルーチンがあります。

### <a name="equivalence-of-iswctypec-desc-to-other-isw-testing-routines"></a>iswctype(c, desc) と同等のその他の isw テスト ルーチン

|*desc* 引数の値|iswctype( *c, desc* ) と同等|
|------------------------------|----------------------------------------|
|**_ALPHA**|**iswalpha(** `c` **)**|
|**_ALPHA** &#124; **_DIGIT**|**iswalnum(** `c` **)**|
|**_BLANK**|**iswblank(** `c` **)**|
|**_CONTROL**|**iswcntrl(** `c` **)**|
|**_DIGIT**|**iswdigit(** `c` **)**|
|**_ALPHA** &#124; **_DIGIT** &#124; **_PUNCT**|**iswgraph(** `c` **)**|
|**_LOWER**|**iswlower(** `c` **)**|
|**_ALPHA** &#124; **_BLANK** &#124; **_DIGIT** &#124; **_PUNCT**|**iswprint(** `c` **)**|
|**_PUNCT**|**iswpunct(** `c` **)**|
|**_BLANK**|**iswblank(** `c` **)**|
|**_SPACE**|**iswspace(** `c` **)**|
|**_UPPER**|**iswupper(** `c` **)**|
|**_HEX**|**iswxdigit(** `c` **)**|

`iswdigit`<br/>
10 進数字に対応するワイド文字。

`iswgraph`<br/>
空白ワイド文字 (L' ') を除く印刷できるワイド文字。

`iswlower`<br/>
小文字、または `iswcntrl`、`iswdigit`、`iswpunct`、`iswspace` がいずれも 0 になるワイド文字の実装定義セットに含まれる文字。 `iswlower` は、小文字に対応するワイド文字に対してのみ、0 以外の値を返します。

`iswprint`<br/>
空白ワイド文字 (L' ') を含む印刷できるワイド文字。

`iswpunct`<br/>
空白ワイド文字 (L' ') および `iswalnum` が 0 以外になるワイド文字を除く、印刷できるワイド文字。

`iswspace`<br/>
標準の空白文字に対応するワイド文字、または `iswalnum` が false になるワイド文字の実装定義セットに含まれるワイド文字。 標準の空白文字は、スペース (L' ')、フォーム フィード (L'\f')、改行 (L'\n')、復帰 (L'\r')、水平タブ (L'\t')、および垂直タブ (L'\v') です。

`iswupper`<br/>
大文字のワイド文字、または `iswcntrl`、`iswdigit`、`iswpunct`、または `iswspace` がいずれも 0 になるワイド文字の実装定義セットに含まれるワイド文字。 `iswupper` は、大文字に対応するワイド文字に対してのみ、0 以外の値を返します。

`iswxdigit`<br/>
16 進数字に対応するワイド文字。

## <a name="example"></a>例

```C
// crt_isfam.c
/* This program tests all characters between 0x0
* and 0x7F, then displays each character with abbreviations
* for the character-type codes that apply.
*/

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   for( ch = 0; ch <= 0x7F; ch++ )
   {
      printf( "%.2x  ", ch );
      printf( " %c", isprint( ch )  ? ch   : ' ' );
      printf( "%4s", isalnum( ch )  ? "AN" : "" );
      printf( "%3s", isalpha( ch )  ? "A"  : "" );
      printf( "%3s", __isascii( ch )  ? "AS" : "" );
      printf( "%3s", iscntrl( ch )  ? "C"  : "" );
      printf( "%3s", __iscsym( ch )  ? "CS "  : "" );
      printf( "%3s", __iscsymf( ch )  ? "CSF"  : "" );
      printf( "%3s", isdigit( ch )  ? "D"  : "" );
      printf( "%3s", isgraph( ch )  ? "G"  : "" );
      printf( "%3s", islower( ch )  ? "L"  : "" );
      printf( "%3s", ispunct( ch )  ? "PU" : "" );
      printf( "%3s", isspace( ch )  ? "S"  : "" );
      printf( "%3s", isprint( ch )  ? "PR" : "" );
      printf( "%3s", isupper( ch )  ? "U"  : "" );
      printf( "%3s", isxdigit( ch ) ? "X"  : "" );
      printf( ".\n" );
   }
}
```

## <a name="output"></a>Output

```Output
00            AS  C                              .
01            AS  C                              .
02            AS  C                              .
03            AS  C                              .
04            AS  C                              .
05            AS  C                              .
06            AS  C                              .
07            AS  C                              .
08            AS  C                              .
09            AS  C                    S         .
0a            AS  C                    S         .
0b            AS  C                    S         .
0c            AS  C                    S         .
0d            AS  C                    S         .
0e            AS  C                              .
0f            AS  C                              .
10            AS  C                              .
11            AS  C                              .
12            AS  C                              .
13            AS  C                              .
14            AS  C                              .
15            AS  C                              .
16            AS  C                              .
17            AS  C                              .
18            AS  C                              .
19            AS  C                              .
1a            AS  C                              .
1b            AS  C                              .
1c            AS  C                              .
1d            AS  C                              .
1e            AS  C                              .
1f            AS  C                              .
20            AS                       S PR      .
21   !        AS              G    PU    PR      .
22   "        AS              G    PU    PR      .
23   #        AS              G    PU    PR      .
24   $        AS              G    PU    PR      .
25   %        AS              G    PU    PR      .
26   &        AS              G    PU    PR      .
27   '        AS              G    PU    PR      .
28   (        AS              G    PU    PR      .
29   )        AS              G    PU    PR      .
2a   *        AS              G    PU    PR      .
2b   +        AS              G    PU    PR      .
2c   ,        AS              G    PU    PR      .
2d   -        AS              G    PU    PR      .
2e   .        AS              G    PU    PR      .
2f   /        AS              G    PU    PR      .
30   0  AN    AS   CS      D  G          PR     X.
31   1  AN    AS   CS      D  G          PR     X.
32   2  AN    AS   CS      D  G          PR     X.
33   3  AN    AS   CS      D  G          PR     X.
34   4  AN    AS   CS      D  G          PR     X.
35   5  AN    AS   CS      D  G          PR     X.
36   6  AN    AS   CS      D  G          PR     X.
37   7  AN    AS   CS      D  G          PR     X.
38   8  AN    AS   CS      D  G          PR     X.
39   9  AN    AS   CS      D  G          PR     X.
3a   :        AS              G    PU    PR      .
3b   ;        AS              G    PU    PR      .
3c   <        AS              G    PU    PR      .
3d   =        AS              G    PU    PR      .
3e   >        AS              G    PU    PR      .
3f   ?        AS              G    PU    PR      .
40   @        AS              G    PU    PR      .
41   A  AN  A AS   CS CSF     G          PR  U  X.
42   B  AN  A AS   CS CSF     G          PR  U  X.
43   C  AN  A AS   CS CSF     G          PR  U  X.
44   D  AN  A AS   CS CSF     G          PR  U  X.
45   E  AN  A AS   CS CSF     G          PR  U  X.
46   F  AN  A AS   CS CSF     G          PR  U  X.
47   G  AN  A AS   CS CSF     G          PR  U   .
48   H  AN  A AS   CS CSF     G          PR  U   .
49   I  AN  A AS   CS CSF     G          PR  U   .
4a   J  AN  A AS   CS CSF     G          PR  U   .
4b   K  AN  A AS   CS CSF     G          PR  U   .
4c   L  AN  A AS   CS CSF     G          PR  U   .
4d   M  AN  A AS   CS CSF     G          PR  U   .
4e   N  AN  A AS   CS CSF     G          PR  U   .
4f   O  AN  A AS   CS CSF     G          PR  U   .
50   P  AN  A AS   CS CSF     G          PR  U   .
51   Q  AN  A AS   CS CSF     G          PR  U   .
52   R  AN  A AS   CS CSF     G          PR  U   .
53   S  AN  A AS   CS CSF     G          PR  U   .
54   T  AN  A AS   CS CSF     G          PR  U   .
55   U  AN  A AS   CS CSF     G          PR  U   .
56   V  AN  A AS   CS CSF     G          PR  U   .
57   W  AN  A AS   CS CSF     G          PR  U   .
58   X  AN  A AS   CS CSF     G          PR  U   .
59   Y  AN  A AS   CS CSF     G          PR  U   .
5a   Z  AN  A AS   CS CSF     G          PR  U   .
5b   [        AS              G    PU    PR      .
5c   \        AS              G    PU    PR      .
5d   ]        AS              G    PU    PR      .
5e   ^        AS              G    PU    PR      .
5f   _        AS   CS CSF     G    PU    PR      .
60   `        AS              G    PU    PR      .
61   a  AN  A AS   CS CSF     G  L       PR     X.
62   b  AN  A AS   CS CSF     G  L       PR     X.
63   c  AN  A AS   CS CSF     G  L       PR     X.
64   d  AN  A AS   CS CSF     G  L       PR     X.
65   e  AN  A AS   CS CSF     G  L       PR     X.
66   f  AN  A AS   CS CSF     G  L       PR     X.
67   g  AN  A AS   CS CSF     G  L       PR      .
68   h  AN  A AS   CS CSF     G  L       PR      .
69   i  AN  A AS   CS CSF     G  L       PR      .
6a   j  AN  A AS   CS CSF     G  L       PR      .
6b   k  AN  A AS   CS CSF     G  L       PR      .
6c   l  AN  A AS   CS CSF     G  L       PR      .
6d   m  AN  A AS   CS CSF     G  L       PR      .
6e   n  AN  A AS   CS CSF     G  L       PR      .
6f   o  AN  A AS   CS CSF     G  L       PR      .
70   p  AN  A AS   CS CSF     G  L       PR      .
71   q  AN  A AS   CS CSF     G  L       PR      .
72   r  AN  A AS   CS CSF     G  L       PR      .
73   s  AN  A AS   CS CSF     G  L       PR      .
74   t  AN  A AS   CS CSF     G  L       PR      .
75   u  AN  A AS   CS CSF     G  L       PR      .
76   v  AN  A AS   CS CSF     G  L       PR      .
77   w  AN  A AS   CS CSF     G  L       PR      .
78   x  AN  A AS   CS CSF     G  L       PR      .
79   y  AN  A AS   CS CSF     G  L       PR      .
7a   z  AN  A AS   CS CSF     G  L       PR      .
7b   {        AS              G    PU    PR      .
7c   |        AS              G    PU    PR      .
7d   }        AS              G    PU    PR      .
7e   ~        AS              G    PU    PR      .
7f            AS  C                              .
```

## <a name="see-also"></a>関連項目

[文字分類](../c-runtime-library/character-classification.md)<br/>
[ロケール](../c-runtime-library/locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[to 系関数](../c-runtime-library/to-functions.md)
