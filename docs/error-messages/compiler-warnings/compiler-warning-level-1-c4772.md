---
title: コンパイラの警告 (レベル 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 95243ab66d5d0296e1c316ff8dde7add75a030cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385460"
---
# <a name="compiler-warning-level-1-c4772"></a>コンパイラの警告 (レベル 1) C4772

> \#インポートが不足しているタイプ ライブラリ; から型を参照'*不足している型*' プレース ホルダーとして使用

タイプ ライブラリが参照された、 [#import](../../preprocessor/hash-import-directive-cpp.md)ディレクティブ。 ただし、タイプ ライブラリがで参照されていませんでしたが、別のタイプ ライブラリへの参照に含まれる`#import`します。 コンパイラによってこの他の .tlb ファイルが見つかりませんでした。

コンパイラが見つけられなかったことタイプ ライブラリで別のディレクトリを使用する場合に注意してください、 [/I (追加インクルード ディレクトリ)](../../build/reference/i-additional-include-directories.md)コンパイラ オプションは、これらのディレクトリを指定します。 コンパイラにタイプ ライブラリを別のディレクトリで検索する場合は、これらのディレクトリを PATH 環境変数に追加します。

既定では、この警告はエラーとして発行されます。 /W0 で C4772 を抑制することはできません。

## <a name="example"></a>例

これは、最初のタイプ ライブラリを C4772 を再現するために必要です。

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

これは、2 つ目のタイプ ライブラリが C4772 を再現するために必要です。

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

次の例では、C4772 が生成されます。

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```