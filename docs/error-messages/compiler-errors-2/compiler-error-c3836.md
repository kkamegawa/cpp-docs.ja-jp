---
title: コンパイラ エラー C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 9c8a7e761f2ece046d5de5c0e74ee911e5ee550d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741405"
---
# <a name="compiler-error-c3836"></a>コンパイラ エラー C3836

静的コンストラクターにメンバー初期化子リストを含めることはできません

マネージクラスは、メンバー初期化リストも持つ静的コンストラクターを持つことはできません。 静的クラスのコンストラクターは、静的データメンバーを初期化して、クラスの初期化を実行するために共通言語ランタイムによって呼び出されます。

## <a name="example"></a>使用例

次の例では、C3836 が生成されます。

```cpp
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
