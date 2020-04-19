---
title: コンパイラの警告 (レベル 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 5e23e6aa69fe8a59e3dfd22af7e33780c223cdd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401606"
---
# <a name="compiler-warning-level-3-c4686"></a>コンパイラの警告 (レベル 3) C4686

> '*ユーザー定義型*': 動作の変更可能な UDT の戻り値の呼び出し規則

## <a name="remarks"></a>Remarks

クラス テンプレートの特殊化されていない戻り値の型で使用する前に定義されます。 C4686; を解決するには、クラスをインスタンス化するものインスタンスの宣言またはメンバーへのアクセス (C\<int >:: 何も) もオプションです。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

## <a name="example"></a>例

以下をお試し代わりにします。

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```