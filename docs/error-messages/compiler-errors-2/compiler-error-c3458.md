---
title: コンパイラ エラー C3458
ms.date: 11/04/2016
f1_keywords:
- C3458
helpviewer_keywords:
- C3458
ms.assetid: 940202fd-8dcc-4042-9c96-3f9e9127d2f1
ms.openlocfilehash: 98f3dc8ec880a2d134da4cc1438841744b8d9a94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756657"
---
# <a name="compiler-error-c3458"></a>コンパイラ エラー C3458

'attribute1': 'construct' に対して属性 'attribute2' は既に指定されています

相互に排他的である 2 つの属性が、同じコンストラクトに指定されました。

## <a name="example"></a>使用例

次の例では C3458 が生成されます。

```cpp
// C3458.cpp
// compile with: /clr /c
[System::Reflection::DefaultMember("Chars")]
public ref class MyString {
public:
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3458
   property char default[int] {
      char get(int index);
      void set(int index, char c);
   }
};
```
