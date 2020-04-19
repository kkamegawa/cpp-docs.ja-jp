---
title: コンパイラエラー C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: d679ce0df0d43772a6c32aa8e00869ac1a4a082b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759647"
---
# <a name="compiler-error-c2743"></a>コンパイラエラー C2743

' type ': __clrcall デストラクターまたはコピーコンストラクターでネイティブ型をキャッチすることはできません

**/Clr**でコンパイルされたモジュールがネイティブ型の例外をキャッチしようとしましたが、型のデストラクターまたはコピーコンストラクターが `__clrcall` 呼び出し規約を使用しています。

**/Clr**を指定してコンパイルする場合、例外処理では、ネイティブ型のメンバー関数が[__clrcall](../../cpp/clrcall.md)ではなく[__cdecl](../../cpp/cdecl.md)されることを想定しています。 `__clrcall` 呼び出し規約を使用するメンバー関数を持つネイティブ型は、 **/clr**でコンパイルされたモジュールでキャッチできません。

詳細については、「[/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C2743 が生成されます。

```cpp
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```
