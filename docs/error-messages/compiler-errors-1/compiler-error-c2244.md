---
title: コンパイラ エラー C2244
ms.date: 11/04/2016
f1_keywords:
- C2244
helpviewer_keywords:
- C2244
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
ms.openlocfilehash: 97ff469c6f3f766bd1b5412133003bae2acaddfc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759478"
---
# <a name="compiler-error-c2244"></a>コンパイラ エラー C2244

' identifier ': 関数の定義を既存の宣言と一致させることができません

単項 + 演算子の使用が、かっこを持たない関数呼び出しの前に使用されました。

このエラーは、プロジェクトC++でのみ発生します。

次の例では、C2244 が生成されます。

```cpp
// C2244.cpp
int func(char) {
   return 0;
}

int func(int) {
   return 0;
}

int main() {
   +func;   // C2244
}
```

C2244 は、クラステンプレートのメンバー関数に無効な関数シグネチャが使用されている場合にも発生する可能性があります。

```cpp
// C2244b.cpp
// compile with: /c
template<class T>
class XYZ {
   void func(T t);
};

template<class T>
void XYZ<T>::func(int i) {}   // C2244 wrong function signature
// try the following line instead
// void XYZ<T>::func(T t) {}
```

C2244 は、メンバー関数テンプレートに無効な関数シグネチャが使用されている場合にも発生する可能性があります。

```cpp
// C2244c.cpp
// compile with: /c
class ABC {
   template<class T>
   void func(int i, T t);
};

template<class T>
void ABC::func(int i) {}   // C2244 wrong signature
// try the following line instead
// void ABC::func(int i, T t) {}
```

関数テンプレートを部分的に特殊化することはできません。

```cpp
// C2244d.cpp
template<class T, class U>
class QRS {
   void func(T t, U u);
};

template<class T>
void QRS<T,int>::func(T t, int u) {}   // C2244
```
