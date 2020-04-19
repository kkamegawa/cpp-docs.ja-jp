---
title: コンパイラの警告 (レベル 2 および 4) C4200
ms.date: 11/04/2016
f1_keywords:
- C4200
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
ms.openlocfilehash: 56a2ba641df610519949f64f6feeca18d9a99e93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359957"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>コンパイラの警告 (レベル 2 および 4) C4200

非標準の拡張機能が使用されています : 構造体または共用体中にサイズが 0 の配列があります。

構造体または共用体がサイズが 0 の配列が含まれていることを示します。

サイズが 0 の配列の宣言は、Microsoft 拡張機能です。 これにより、C ファイルをコンパイルした場合はレベル 2 の警告、C++ ファイルをコンパイルした場合はレベル 4 の警告が発生します。 C++コンパイルでは、この警告も提供します。「演算子を生成できません、copy-ctor または copy-assignment UDT にサイズが 0 の配列が含まれている場合。」 次の例では警告 C4200 が生成されます。

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

この非標準の拡張機能は、可変長の外部データ構造とのインターフェイス コードによく使用されます。 コードがこのシナリオに該当する場合は、次のように警告を無効にできます。

## <a name="example"></a>例

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```