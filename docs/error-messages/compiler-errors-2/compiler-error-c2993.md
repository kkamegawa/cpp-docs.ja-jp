---
title: コンパイラ エラー C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5aa0d27b2d469f53ec521f587172398b7d4c2d1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761232"
---
# <a name="compiler-error-c2993"></a>コンパイラ エラー C2993

' identifier ': 非型テンプレートパラメーター ' parameter ' の型が正しくありません。

構造体または共用体の引数を持つテンプレートを宣言することはできません。 ポインターを使用して、構造体と共用体をテンプレートパラメーターとして渡します。

次の例では、C2993 が生成されます。

```cpp
// C2993.cpp
// compile with: /c
// C2993 expected
struct MyStruct {
   int a;char b;
};

template <class T, struct MyStruct S>   // C2993

// try the following line instead
// template <class T, struct MyStruct * S>
class CMyClass {};
```

このエラーは、Visual Studio .NET 2003 で実行されたコンパイラ準拠作業の結果としても生成されます。浮動小数点の非型テンプレートパラメーターは使用できなくなりました。 標準C++では、浮動小数点の非型テンプレートパラメーターは許可されません。

関数テンプレートの場合は、関数の引数を使用して、浮動小数点型以外のテンプレートパラメーターを渡します (このコードは、visual Studio .NET 2003 および visual Studio .NET バージョンのC++visual で有効になります)。 クラステンプレートの場合は、簡単な回避策はありません。

```cpp
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```
