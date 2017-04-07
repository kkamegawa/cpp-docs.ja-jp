---
title: "vscanf_s、vwscanf_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vscanf_s"
  - "vwscanf_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_vtscanf_s"
  - "vscanf_s"
  - "vwscanf_s"
dev_langs: 
  - "C++"
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# vscanf_s、vwscanf_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標準入力ストリームから書式付きデータを読み取ります。  [vscanf、vwscanf](../../c-runtime-library/reference/vscanf-vwscanf.md) のこれらのバージョンは、「[CRT のセキュリティ機能](../Topic/Security%20Features%20in%20the%20CRT.md)」に説明されているように、セキュリティが強化されています。  
  
## 構文  
  
```  
int vscanf_s(  
   const char *format,  
   va_list arglist  
);   
int vwscanf_s(  
   const wchar_t *format,  
   va_list arglist  
);  
```  
  
#### パラメーター  
 `format`  
 書式指定文字列。  
  
 `arglist`  
 可変個引数リスト。  
  
## 戻り値  
 正常に変換され、代入されたフィールドの数を返します。この数には、読み取られても代入されなかったフィールドは含まれません。  戻り値が 0 の場合は、代入されたフィールドがなかったことを示します。  エラーが発生した場合や、まだ文字を読み取っていないときにファイルの終端文字または文字列の終端文字が検出された場合は、`EOF` \(end\-of\-file\) を返します。  `format` が `NULL` ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。  実行の継続が許可された場合、`vscanf_s` および `vwscanf_s` は `EOF` を返し、`errno` を `EINVAL` に設定します。  
  
 エラー コードの詳細については、「[errno、\_doserrno、\_sys\_errlist、および \_sys\_nerr](../Topic/errno,%20_doserrno,%20_sys_errlist,%20and%20_sys_nerr.md)」を参照してください。  
  
## 解説  
 `vscanf_s` 関数は、標準入力ストリーム `stdin` からデータを読み取り、そのデータを `arglist` 引数リストで指定されている位置に書き込みます。  リストの各引数は、`format` の型指定子に対応する型の変数へのポインターにする必要があります。  重なり合う文字列間でコピーした場合の動作は未定義です。  
  
 `vwscanf_s` 関数は、`vscanf_s` 関数のワイド文字バージョンです。`vwscanf_s` 関数の引数 `format` は、ワイド文字列です。  ストリームが ANSI モードで開かれている場合、`vwscanf_s` と `vscanf_s` の動作は同じになります。  `vscanf_s` では、UNICODE ストリームからの入力はサポートされていません。  
  
 `vscanf` および `vwscanf` とは異なり、`vscanf_s` および `vwscanf_s` では、`c`、`C`、`s`、`S` の各型、または `[]` で囲まれた文字列コントロール セットのすべての入力パラメーターに対してバッファー サイズを指定する必要があります。  バッファー サイズ \(文字単位\) は、バッファーまたは変数のポインターの直後に追加パラメーターとして渡されます。  `wchar_t` 文字列のバッファー サイズ \(文字単位\) は、バイト単位のサイズと同じではありません。  
  
 バッファー サイズには、終端 null も含まれます。  幅指定フィールドを使用して、読み取られたトークンがバッファーに確実に収まるようにすることができます。  幅指定フィールドが使用されない場合で、読み取られたトークンがバッファーに収まらない場合、そのバッファーには何も書き込まれません。  
  
> [!NOTE]
>  サイズ パラメーターは `size_t` 型ではなく、`unsigned` 型です。  
  
 詳細については、「[scanf 関数の文字幅指定](../../c-runtime-library/scanf-width-specification.md)」を参照してください。  
  
### 汎用テキスト ルーチンのマップ  
  
|TCHAR.H のルーチン|\_UNICODE & \_MBCS が未定義の場合|\_MBCS が定義されている場合|\_UNICODE が定義されている場合|  
|-------------------|--------------------------------|-----------------------|--------------------------|  
|`_vtscanf_s`|`vscanf_s`|`vscanf_s`|`vwscanf_s`|  
  
 詳細については、「[scanf 関数と wscanf 関数の書式指定フィールド](../Topic/Format%20Specification%20Fields:%20scanf%20and%20wscanf%20Functions.md)」を参照してください。  
  
## 必要条件  
  
|ルーチン|必須ヘッダー|  
|----------|------------|  
|`vscanf_s`|\<stdio.h\>|  
|`wscanf_s`|\<stdio.h\> または \<wchar.h\>|  
  
 コンソールは、[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] アプリではサポートされていません。  コンソール \(`stdin`、`stdout`、および `stderr`\) に関連付けられている標準ストリームのハンドルは、C ランタイム関数によって [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] アプリで使用する前に、リダイレクトする必要があります。  互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。  
  
## 使用例  
  
```  
// crt_vscanf_s.c  
// compile with: /W3  
// This program uses the vscanf_s and vwscanf_s functions  
// to read formatted input.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
int call_vscanf_s(char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vscanf_s(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int call_vwscanf_s(wchar_t *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vwscanf_s(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    int   i, result;  
    float fp;  
    char  c, s[81];  
    wchar_t wc, ws[81];  
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,  
                           &wc, 1, s, _countof(s), ws, _countof(ws) );  
    printf( "The number of fields input is %d\n", result );  
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);  
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,  
                            &wc, 1, s, _countof(s), ws, _countof(ws) );  
    wprintf( L"The number of fields input is %d\n", result );  
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);  
}  
  
```  
  
 このプログラムで、この例の入力を指定した場合、次の出力が生成されます。  
  
 `71 98.6 h z Byte characters`  
  
 `36 92.3 y n Wide characters`  
  
  **フィールドの入力数は 6 です**  
**内容: 71 98.599998 h z バイトの文字**  
**フィールドの入力数は 6 です**  
**内容: 36 92.300003 y n 幅の文字**   
## 同等の .NET Framework 関数  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
-   [System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)  
  
-   [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx) などの `Parse` メソッドも参照してください。  
  
## 参照  
 [浮動小数点サポート](../../c-runtime-library/floating-point-support.md)   
 [ストリーム入出力](../../c-runtime-library/stream-i-o.md)   
 [ロケール](../../c-runtime-library/locale.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [vscanf、vwscanf](../../c-runtime-library/reference/vscanf-vwscanf.md)