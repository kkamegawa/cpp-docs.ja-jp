---
title: コンパイラの警告 (レベル 4) C4263
ms.date: 11/04/2016
f1_keywords:
- C4263
helpviewer_keywords:
- C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
ms.openlocfilehash: ed4b8561975f3d808781551e0d5f363d0d0088b8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991439"
---
# <a name="compiler-warning-level-4-c4263"></a>コンパイラの警告 (レベル 4) C4263

' function ': メンバー関数は、基底クラスの仮想メンバー関数をオーバーライドしません

クラス関数の定義の名前が基底クラスの仮想関数と同じですが、同じ数または型の引数を指定することはできません。 これにより、実質的に基本クラスの仮想関数が非表示になります。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では、C4263 が生成されます。

```cpp
// C4263.cpp
// compile with: /W4
#pragma warning(default:4263)
#pragma warning(default:4264)
class B {
public:
   virtual void func();
};

class D : public B {
   void func(int);   // C4263
};

int main() {
}
```
