---
title: コンパイラ エラー C3227
ms.date: 11/04/2016
f1_keywords:
- C3227
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
ms.openlocfilehash: 460000531dba77e42379199f276c9e2e02f43a9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743420"
---
# <a name="compiler-error-c3227"></a>コンパイラ エラー C3227

' parameter ': ジェネリック型を割り当てるために ' keyword ' を使用することはできません

型をインスタンス化するには、適切なコンストラクターが必要です。 ただし、コンパイラは適切なコンストラクターが使用可能であることを確認できません。

ジェネリックではなくテンプレートを使用してこのエラーを解決することも、複数のメソッドのいずれかを使用して型のインスタンスを作成することもできます。

## <a name="example"></a>使用例

次の例では、C3227 が生成されます。

```cpp
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```
