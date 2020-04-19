---
title: コンパイラの警告 (レベル 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: cca2f8cc13cc8317bac3736e142ef58e126ed994
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390491"
---
# <a name="compiler-warning-level-1-c4382"></a>コンパイラの警告 (レベル 1) C4382

> スロー '*型*': _ _clrcall デストラクターまたはコピー コンス トラクターを持つ型のみを/clr でキャッチできます純粋なモジュール。

## <a name="remarks"></a>Remarks

**/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

コンパイルされたときに **/clr** (いない **/clr: 純粋な**)、例外処理には、メンバー関数は、ネイティブ型にするにが必要です[_ _cdecl](../../cpp/cdecl.md)なく[_ _clrcall](../../cpp/clrcall.md). ネイティブ型を使用してメンバー関数で`__clrcall`でコンパイルされたモジュールの呼び出し規約をキャッチできない **/clr**します。

コンパイルされたモジュールで、例外がキャッチされるかどうか **/clr: 純粋な**、この警告を無視することができます。

詳細については、「[/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4382 が生成されます。

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```