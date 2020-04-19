---
title: コンパイラの警告 (レベル 1) C4162
ms.date: 11/04/2016
f1_keywords:
- C4162
helpviewer_keywords:
- C4162
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
ms.openlocfilehash: 7e70898065a40a965b08b090bc59263acd918515
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624851"
---
# <a name="compiler-warning-level-1-c4162"></a>コンパイラの警告 (レベル 1) C4162

' identifier ': C リンケージを伴う関数が見つかりませんでした

C リンケージを持つ関数が宣言されていますが、見つかりません。

この警告を解決するには、.c ファイル (C コンパイラを呼びます) でコンパイルします。  C++コンパイラを呼び出す必要がある場合は、関数宣言の前に Extern "C" を配置します。

次の例では、C4162 が生成されます。

```cpp
// C4162.cpp
// compile with: /c /W1
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)   // C4162

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```

考えられる解決方法:

```cpp
// C4162b.cpp
// compile with: /c
extern "C"
unsigned char _bittest(long* a, long b);
#pragma intrinsic (_bittest)

int main() {
   bool bit;
   long num = 78002;
   bit = _bittest(&num, 5);
}
```