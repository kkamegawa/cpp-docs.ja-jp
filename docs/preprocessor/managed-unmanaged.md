---
title: マネージド、アンマネージド プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 4c13155d1c84966a593df11baf525a0c3539f02c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218816"
---
# <a name="managed-unmanaged-pragmas"></a>マネージド、アンマネージド プラグマ

関数レベルの制御を有効にして、関数をマネージまたはアンマネージとしてコンパイルします。

## <a name="syntax"></a>構文

> **マネージド #pragma**\
> **アンマネージ #pragma**\
> **#pragma 管理 (** **[プッシュ,]** { **on** | **off** } **)** \
> **#pragma マネージ (pop)**

## <a name="remarks"></a>Remarks

[/Clr](../build/reference/clr-common-language-runtime-compilation.md)コンパイラオプションは、関数をマネージまたはアンマネージとしてコンパイルするためのモジュールレベルのコントロールを提供します。

アンマネージ関数は、ネイティブプラットフォーム用にコンパイルされます。 プログラムのその部分の実行は、共通言語ランタイムによってネイティブプラットフォームに渡されます。

関数は、`/clr` が使用されると、既定でマネージとしてコンパイルされます。

これらのプラグマを適用するときは次のようにします。

- 関数の前にプラグマを追加しますが、関数本体内には追加しません。

- `#include` ステートメントの後にプラグマを追加します。 ステートメントの前に`#include`これらのプラグマを使用しないでください。

コンパイルでが使用されていない`/clr`場合、コンパイラは**マネージ**プラグマおよび**アンマネージ**プラグマを無視します。

テンプレート関数がインスタンス化されると、テンプレートが定義されているときのプラグマの状態によって、マネージとアンマネージのどちらであるかが決まります。

詳細については、「[混在アセンブリの初期化](../dotnet/initialization-of-mixed-assemblies.md)」を参照してください。

## <a name="example"></a>例

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
