---
title: DLL の境界を越えて CRT オブジェクトを渡す場合に発生する可能性のあるエラー
ms.date: 11/04/2016
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: 10fbb128698b6422779d09a15fe3c1d25e8de5b5
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446655"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>DLL の境界を越えて CRT オブジェクトを渡す場合に発生する可能性のあるエラー

ファイル ハンドル、ロケール、環境変数などの C ランタイム (CRT) オブジェクトを DLL の境界を越えて渡す場合 (DLL の境界を越えた関数の呼び出し)、DLL またはその DLL を呼び出すファイルが異なる CRT ライブラリのコピーを使用していると、予想外の動作が発生する可能性があります。

メモリを (`new` または `malloc` で明示的に、または `strdup`、`strstreambuf::str` で暗黙的に割り当てるなどして) 割り当てたうえで、DLL の境界を越えてポインターを渡してそこで解放した場合にも、同じような問題が発生する可能性があります。 これは、DLL とそのユーザーが異なる CRT ライブラリのコピー使用している場合、メモリ アクセス違反、またはヒープ破損の原因になります。

この問題の別の兆候には、次のようなデバッグ中の出力ウィンドウのエラーがあります。

HEAP[]:Invalid Address specified to RtlValidateHeap(#,#)

## <a name="causes"></a>原因

CRT ライブラリのコピーはそれぞれ状態が異なります。アプリまたは DLL により、スレッド ローカル ストレージに保存されます。 そのため、ファイル ハンドル、環境変数、ロケールなどの CRT オブジェクトは、オブジェクトが割り当てられている、または設定されているアプリまたは DLL の CRT コピーに対してのみ有効になります。 DLL とそのアプリ クライアントで CRT ライブラリの異なるコピーが使用されているとき、DLL 境界を越えてそのような CRT オブジェクトを渡しても、向こう側で正しく取得されることは期待できません。 これは特に、Visual Studio 2015 以降で、Universal CR より前のバージョンの CRT に当てはまります。 Visual Studio 2013 以前で構築されたあらゆるバージョンの Visual Studio について、バージョン固有の CRT ライブラリがありました。 データ構造や命名規則など、CRT の内部実装詳細はバージョンごとに異なります。 あるバージョンの CRT のためにコンパイルされたコードを別のバージョンの CRT DLL に動的にリンクすることは以前はできませんでした。動的にリンクされる場合もありましたが、それは偶然であり、設計によるものではありませんでした。

また、CRT ライブラリの各コピーには独自のヒープ マネージャーが与えられているため、1 つの CRT ライブラリでメモリを割り当て、DLL 境界を越えてポインターを渡し、CRT ライブラリの別のコピーで解放すると、ヒープ破損の原因になることがあります。 境界を越えて CRT オブジェクトを渡すか、メモリを割り当て、DLL の外でそれを解放することを要求するように DLL を設計する場合、DLL と同じ CRT ライブラリ コピーを使用するように DLL のアプリ クライアントを制限します。 DLL とそのクライアントは通常、読み込み時に両方とも同じバージョンの CRT DLL にリンクされている場合にのみ、CRT ライブラリの同じコピーを使用します。 Windows 10 で Visual Studio 2015 以降により使用される Universal CRT ライブラリの DLL バージョンが現在、一元的に配置される Windows コンポーネント、ucrtbase.dll になったため、Visual Studio 2015 以降のバージョンで開発されたアプリで同じになります。 ただし、CRT コードが同じでも、あるヒープで割り当てられたメモリを別のヒープを使用するコンポーネントに渡すことはできません。

## <a name="example"></a>例

### <a name="description"></a>説明

この例では、DLL 境界を越えてファイル ハンドルが渡されます。

DLL と .exe ファイルは /MD で開発されます。そのため、1 つのコピーの CRT を共有します。

CRT の個別コピーを使用するように /MT で再構築すると、結果的に生成される test1Main.exe を実行したときにアクセス違反が発生します。

```cpp
// test1Dll.cpp
// compile with: cl /EHsc /W4 /MD /LD test1Dll.cpp
#include <stdio.h>
__declspec(dllexport) void writeFile(FILE *stream)
{
   char   s[] = "this is a string\n";
   fprintf( stream, "%s", s );
   fclose( stream );
}
```

```cpp
// test1Main.cpp
// compile with: cl /EHsc /W4 /MD test1Main.cpp test1Dll.lib
#include <stdio.h>
#include <process.h>
void writeFile(FILE *stream);

int main(void)
{
   FILE  * stream;
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );
   writeFile(stream);
   system( "type fprintf.out" );
}
```

```Output
this is a string
```

## <a name="example"></a>例

### <a name="description"></a>説明

この例では、DLL の境界を越えて環境変数が渡されます。

```cpp
// test2Dll.cpp
// compile with: cl /EHsc /W4 /MT /LD test2Dll.cpp
#include <stdio.h>
#include <stdlib.h>

__declspec(dllexport) void readEnv()
{
   char *libvar;
   size_t libvarsize;

   /* Get the value of the MYLIB environment variable. */
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );

   if( libvar != NULL )
      printf( "New MYLIB variable is: %s\n", libvar);
   else
      printf( "MYLIB has not been set.\n");
   free( libvar );
}
```

```cpp
// test2Main.cpp
// compile with: cl /EHsc /W4 /MT test2Main.cpp test2dll.lib
#include <stdlib.h>
#include <stdio.h>

void readEnv();

int main( void )
{
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );
   readEnv();
}
```

```Output
MYLIB has not been set.
```

CRT のコピーが 1 つだけ使用されるように DLL と .exe ファイルの両方が構築されている場合、このプログラムは正常に実行され、次が出力されます。

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>関連項目

[CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)
