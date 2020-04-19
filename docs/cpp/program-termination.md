---
title: C++プログラムの終了
description: 言語プログラムをC++exit する方法について説明します。
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- exit
- abort
- return
- main
- atexit
- void
ms.openlocfilehash: f83c9d5da5b0a1127603a97fd7946e9cca43a7a5
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123956"
---
# <a name="c-program-termination"></a>C++プログラムの終了

でC++は、次の方法でプログラムを exit できます。

- [exit](exit-function.md)関数を呼び出します。
- [abort](abort-function.md)関数を呼び出します。
- `main`から[return](return-statement-cpp.md)ステートメントを実行します。

## <a name="opno-locexit-function"></a>exit 関数

\<stdlib.h> > で宣言された[exit](../c-runtime-library/reference/exit-exit-exit.md)関数は、プログラムをC++終了します。 `exit` の引数として指定された値は、プログラムの return コードまたは exit コードとしてオペレーティングシステムに返されます。 規則により、return コードがゼロの場合は、プログラムが正常に完了したことを意味します。 \<stdlib.h> > で定義されている定数 EXIT_FAILURE と EXIT_SUCCESS を使用して、プログラムの成功または失敗を示すことができます。

`main` 関数から **return** ステートメントを発行することは、return 値を引数として `exit` 関数を呼び出すことと同じです。

## <a name="opno-locabort-function"></a>abort 関数

[abort](../c-runtime-library/reference/abort.md)関数は、標準のインクルードファイル \<stdlib.h> > でも宣言されており、 C++プログラムを終了します。 `exit` と `abort` の違いは、`exit` によってC++実行時の終了処理を実行できることです (グローバルオブジェクトのデストラクターが呼び出されます)。一方、`abort` はプログラムをすぐに終了します。 `abort` 関数は、初期化されたグローバル静的オブジェクトの通常の破棄プロセスをバイパスします。 また、 [atexit](../c-runtime-library/reference/atexit.md)関数を使用して指定された特別な処理をバイパスします。

## <a name="opno-locatexit-function"></a>atexit 関数

[atexit](../c-runtime-library/reference/atexit.md)関数を使用して、プログラムを終了する前に実行するアクションを指定します。 exit処理関数を実行する前に、 **atexit** の呼び出しの前に初期化されたグローバルな静的オブジェクトは破棄されません。

## <a name="opno-locreturn-statement-in-opno-locmain"></a>main 内の return ステートメント

`main` から[return](return-statement-cpp.md)ステートメントを発行することは、`exit` 関数を呼び出すことと機能的には同じです。 次に例を示します。

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

前の例の `exit` および **return** ステートメントは機能的には同じです。 ただし、 C++では、 **void** 以外の return 型を持つ関数に値 return 必要があります。 **return** ステートメントを使用すると、`main`の値を return できます。

## <a name="destruction-of-static-objects"></a>静的オブジェクトの破棄

`exit` を呼び出したとき、または `main`から **return** ステートメントを実行すると、静的オブジェクトは初期化の逆の順序 (存在する場合は `atexit` の呼び出しの後) で破棄されます。 次の例は、こうした初期化やクリーンアップがどのように機能するのかを示します。

### <a name="example"></a>使用例

次の例では、`main`に入る前に、静的オブジェクト `sd1` および `sd2` が作成され、初期化されます。 このプログラムが **return** ステートメントを使用して終了すると、最初に `sd2` が破棄され、`sd1`ます。 `ShowData` クラスのデストラクターは、これらの静的オブジェクトに関連付けられたファイルを閉じます

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

このコードを作成するもう 1 つの方法は、ブロック スコープを持つ `ShowData` オブジェクトを宣言して、スコープ外に出ると破棄できるようにすることです。

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>関連項目

[main 関数とコマンドライン引数](main-function-command-line-args.md)
