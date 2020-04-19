---
title: コンパイラの警告 (レベル 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 012866e328433ec9511782c26a39265481ff4940
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386513"
---
# <a name="compiler-warning-level-1-c4067"></a>コンパイラの警告 (レベル 1) C4067

> 予期しないトークン - 次のプリプロセッサ ディレクティブには、改行が必要です。

## <a name="remarks"></a>Remarks

コンパイラは、検出し、余分な文字が次のプリプロセッサ ディレクティブは無視されます。 一般的な原因は、ディレクティブの後、無効なセミコロンは、予期しない文字によって発生ことができます。 コメントでは、この警告は発生しません。 **/Za**コンパイラ オプションは、既定の設定よりも詳細のプリプロセッサ ディレクティブには、この警告を使用できます。

## <a name="example"></a>例

```cpp
// C4067a.cpp
// compile with: cl /EHsc /DX /W1 /Za C4067a.cpp
#include <iostream>
#include <string> s     // C4067
#if defined(X);         // C4067
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif;                 // C4067 only under /Za
int main()
{
    std::cout << s << std::endl;
}
```

この警告を解決するのには、無効な文字を削除またはコメント ブロックに移動します。 削除することによって特定 C4067 の警告を無効にすることがあります、 **/Za**コンパイラ オプション。

```cpp
// C4067b.cpp
// compile with: cl /EHsc /DX /W1 C4067b.cpp
#include <iostream>
#include <string>
#if defined(X)
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif
int main()
{
    std::cout << s << std::endl;
}
```