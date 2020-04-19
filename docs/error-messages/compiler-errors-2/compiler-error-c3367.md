---
title: コンパイラ エラー C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: f53312fa9225270ef79d50d2ad351adce790d6fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300538"
---
# <a name="compiler-error-c3367"></a>コンパイラ エラー C3367

'static_member_function': バインドされていないデリゲートを作成するために静的関数を使用することはできません

バインドされていないデリゲートを呼び出す場合は、オブジェクトのインスタンスを渡す必要があります。 静的メンバー関数はクラス名によって呼び出されるので、バインドされていないデリゲートは、インスタンス メンバー関数でのみインスタンス化できます。

バインドされていないデリゲートの詳細については、次を参照してください。[方法。定義し、デリゲートを使用して (C++/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)します。

## <a name="example"></a>例

次の例では C3367 が生成されます。

```cpp
// C3367.cpp
// compile with: /clr
ref struct R {
   void b() {}
   static void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::b);   // OK
   Del ^ b = gcnew Del(&R::f);   // C3367
}
```