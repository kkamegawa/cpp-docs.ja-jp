---
title: コンパイラの警告 C4957
ms.date: 11/04/2016
f1_keywords:
- C4957
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
ms.openlocfilehash: 79a1b516db1508c755693b67ca2e4070095839da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388668"
---
# <a name="compiler-warning-c4957"></a>コンパイラの警告 C4957

> '*キャスト*': 明示的なキャストを'*cast_from*'to'*できません*' は、検証できません

## <a name="remarks"></a>Remarks

キャストにより、検証不可能なイメージが生成されます。

安全なキャストもあります (ユーザー定義の変換をトリガーする `static_cast` 、 `const_cast`など)。 [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) は、検証可能なコードを生成することが保証されています。

詳細については、次を参照してください。[純粋で検証可能なコード (C +/cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)します。

**/Clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

この警告は、エラーとして表示されます。無効にするには、 [warning](../../preprocessor/warning.md) プラグマ、または [/wd](../../build/reference/compiler-option-warning-level.md) コンパイラ オプションを使用します。

## <a name="example"></a>例

次の例では C4957 が生成されます。

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```