---
title: コンパイラの警告 (レベル 1) C4490
ms.date: 11/04/2016
f1_keywords:
- C4490
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
ms.openlocfilehash: 41fa124eed365b87b419a4019262c0c673399295
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966180"
---
# <a name="compiler-warning-level-1-c4490"></a>コンパイラの警告 (レベル 1) C4490

' override ': オーバーライド指定子の使い方が正しくありません。' function ' が基本 ref クラスメソッドと一致しません

オーバーライド指定子が正しく使用されませんでした。 たとえば、インターフェイス関数をオーバーライドするのではなく、インターフェイス関数を実装します。

詳細については、「[オーバーライド指定子](../../extensions/override-specifiers-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4490 が生成されます。

```cpp
// C4490.cpp
// compile with: /clr /c /W1

interface struct IFace {
   void Test();
};

ref struct Class1 : public IFace {
   virtual void Test() override {}   // C4490
   // try the following line instead
   // virtual void Test() {}
};
```