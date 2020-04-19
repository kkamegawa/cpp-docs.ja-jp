---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: a147af8f536923082df3a2d6d332150a57d6af1b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857386"
---
# <a name="novtable"></a>novtable

**Microsoft 固有の仕様**

これは **__declspec**拡張属性です。

この形式の **__declspec**は、任意のクラス宣言に適用できますが、純粋なインターフェイスクラス、つまり独自にインスタンス化されないクラスにのみ適用する必要があります。 **__Declspec**により、コンパイラは、コンストラクターおよびクラスのデストラクターで vfptr を初期化するコードを生成しなくなります。 多くの場合、これは、クラスに関連付けられている vtable への参照のみを削除するので、リンカーはこれを削除します。 この形式の **__declspec**を使用すると、コードサイズが大幅に削減される可能性があります。

**Novtable**でマークされたクラスをインスタンス化してからクラスメンバーにアクセスしようとすると、アクセス違反 (AV) が発生します。

## <a name="example"></a>使用例

```cpp
// novtable.cpp
#include <stdio.h>

struct __declspec(novtable) X {
   virtual void mf();
};

struct Y : public X {
   void mf() {
      printf_s("In Y\n");
   }
};

int main() {
   // X *pX = new X();
   // pX->mf();   // Causes a runtime access violation.

   Y *pY = new Y();
   pY->mf();
}
```

```Output
In Y
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)