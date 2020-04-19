---
title: コンパイラの警告 C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: 896fca6c6b257c90ccdf813a9c6cb6bc27ad9e96
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623618"
---
# <a name="compiler-warning-c4485"></a>コンパイラの警告 C4485

' override_function ': 基本 ref クラスメソッド ' base_class_function ' と一致しますが、' new ' または ' override ' に設定されていません。' new ' (および ' virtual ') が想定されています

アクセサーは、基底クラスのアクセサー関数である、`virtual` キーワードの有無にかかわらずオーバーライドします。ただし、`override` または `new` 指定子は、オーバーライドする関数シグネチャの一部ではありませんでした。 この警告を解決するには、`new` または `override` 指定子を追加します。

詳細については、「 [override](../../extensions/override-cpp-component-extensions.md)と[new (vtable の新しいスロット)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) 」を参照してください。

C4485 は常にエラーとして発行されます。 C4485 を抑制するには、 [warning](../../preprocessor/warning.md)プラグマを使用します。

## <a name="example"></a>例

次の例では、C4485 が生成されます。

```cpp
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```