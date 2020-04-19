---
title: コンパイラ エラー C3162
ms.date: 11/04/2016
f1_keywords:
- C3162
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
ms.openlocfilehash: 95cd2c4af614906da7ba2d1c4c5dd488059f970a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761804"
---
# <a name="compiler-error-c3162"></a>コンパイラ エラー C3162

' type ': デストラクターを含む参照型を静的データメンバー ' member ' の型として使用することはできません

共通言語ランタイムは、クラスに静的メンバー関数も含まれている場合に、ユーザー定義のデストラクターを実行するタイミングを認識できません。

オブジェクトを明示的に削除しない限り、デストラクターは実行されません。

詳細については、次のトピックを参照してください。

- [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Visual C++ の 64 ビットへの移行に関する一般的な問題](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>使用例

次の例では、C3162 が生成されます。

```cpp
// C3162.cpp
// compile with: /clr /c
ref struct A {
   ~A() { System::Console::WriteLine("in destructor"); }
   static A i;   // C3162
   static A^ a = gcnew A;   // OK
};

int main() {
   A ^ a = gcnew A;
   delete a;
}
```
