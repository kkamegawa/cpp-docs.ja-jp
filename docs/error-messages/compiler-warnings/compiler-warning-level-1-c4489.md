---
title: コンパイラの警告 (レベル 1) C4489
ms.date: 11/04/2016
f1_keywords:
- C4489
helpviewer_keywords:
- C4489
ms.assetid: 43b51c8c-27b5-44c9-b974-fe4b48f4896f
ms.openlocfilehash: 78ceecb5918ccb74bd61afe62bbf8b542d585f81
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966200"
---
# <a name="compiler-warning-level-1-c4489"></a>コンパイラの警告 (レベル 1) C4489

' 指定子 ': インターフェイスメソッド ' method ' では許可されていません。オーバーライド指定子は、ref クラスおよび値クラスメソッドでのみ使用できます

指定子キーワードがインターフェイスメソッドで正しく使用されませんでした。

詳細については、「[オーバーライド指定子](../../extensions/override-specifiers-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4489 が生成されます。

```cpp
// C4489.cpp
// compile with: /clr /c /W1
public interface class I {
   void f() new;   // C4489
   virtual void b() override;   // C4489

   void g();   // OK
};
```