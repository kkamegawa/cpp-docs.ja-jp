---
title: コンパイラの警告 (レベル 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 9681408841173bad4aca3305e727ddde6cd98f14
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966168"
---
# <a name="compiler-warning-level-1-c4383"></a>コンパイラの警告 (レベル 1) C4383

' instance_dereference_operator ': ユーザー定義の ' operator ' 演算子が存在する場合、ハンドルの逆参照の意味が変更される可能性があります。演算子を静的関数として記述し、オペランドについて明示的にします。

マネージ型の逆参照演算子のユーザー定義インスタンスオーバーライドを追加すると、その型の逆参照演算子がハンドルのオブジェクトを返す機能をオーバーライドする可能性があります。 静的なユーザー定義の逆参照演算子を記述することを検討してください。

詳細については、「[オブジェクト演算子 (^) へのハンドル](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)」および「[参照操作の追跡](../../extensions/tracking-reference-operator-cpp-component-extensions.md)」を参照してください。

また、参照されたメタデータを使用して、他の言語コンパイラでインスタンス演算子を使用することはできません。 詳細については、「[ユーザー定義のC++演算子 (/cli)](../../dotnet/user-defined-operators-cpp-cli.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4383 が生成されます。

```cpp
// C4383.cpp
// compile with: /clr /W1

ref struct S {
   int operator*() { return 0; }   // C4383
};

ref struct T {
   static int operator*(T%) { return 0; }
};

int main() {
   S s;
   S^ pS = %s;

   T t;
   T^ pT = %t;
   T% rT = *pT;
}
```