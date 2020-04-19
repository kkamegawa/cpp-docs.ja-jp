---
title: コンパイラエラー C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 6f548c72a0e95c533ed711fe9f2583a7abd6c500
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760762"
---
# <a name="compiler-error-c3114"></a>コンパイラエラー C3114

' argument ': 有効な名前付き属性引数ではありません

属性クラスのデータメンバーが有効な名前付き引数であるためには、`static`、`const`、または `literal`としてマークすることはできません。 プロパティの場合、プロパティを `static` せずに、get アクセサーと set アクセサーを指定する必要があります。

詳細については、「[プロパティ](../../extensions/property-cpp-component-extensions.md)と[ユーザー定義の属性](../../extensions/user-defined-attributes-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3114 が生成されます。

```cpp
// C3114.cpp
// compile with: /clr /c
public ref class A : System::Attribute {
public:
   static property int StaticProp {
      int get();
   }

   property int Prop2 {
      int get();
      void set(int i);
   }
};

[A(StaticProp=123)]   // C3114
public ref class R {};

[A(Prop2=123)]   // OK
public ref class S {};
```
