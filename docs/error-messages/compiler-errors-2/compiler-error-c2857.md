---
title: コンパイラ エラー C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 10c0ea3b54ded29bf80f83713cea33428dca6ca0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350440"
---
# <a name="compiler-error-c2857"></a>コンパイラ エラー C2857

> '#include' は/Yc で指定されたステートメント*filename*コマンド ライン オプションは、ソース ファイルにありませんでした

[/Yc](../../build/reference/yc-create-precompiled-header-file.md)オプションがコンパイルされるソース ファイルに含まれていないインクルード ファイルの名前を指定します。

## <a name="remarks"></a>Remarks

使用すると、 **/Yc**<em>filename</em>プリコンパイル済みヘッダー (PCH) ファイル、ソース ファイルを作成するソース ファイルでオプションを含める必要があります、 *filename*ヘッダー ファイル。 によって指定されたを含むソース ファイルに含まれるすべてのファイル*filename*、PCH ファイルに挿入されます。 使用してコンパイルされたその他のソース ファイルで、 **/Yu**<em>filename</em> PCH を使用する場合にファイルのインクルード*ファイル名*ファイルの最初のコメントではない行にある必要があります。 コンパイラでは、このインクルードする前にソース ファイル内のあらゆるものは無視されます。

このエラーは、によって発生することができます、 `#include "filename"` PCH ソース ファイルにコンパイルされていない条件付きコンパイル ブロック内のステートメント。

## <a name="example"></a>例

一般的な使用法 で、PCH のソース ファイルと、プロジェクト内の 1 つのソース ファイルが指定されているし、1 つのヘッダー ファイルは、PCH ヘッダー ファイルとして使用します。 一般的な PCH ヘッダー ファイルには、すべてのプロジェクトで使用されるライブラリ ヘッダーはまだ開発中であるローカルではないヘッダーがあります。 このサンプルでは、PCH ヘッダー ファイルの名前は*my_pch.h*します。

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

PCH のソース ファイルを使用してコンパイル、 **/Yc**<em>my_pch.h</em>オプション。 コンパイラがこの PCH ヘッダー ファイルのインクルードを見つけられない場合は、C2857 が生成されます。

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

使用してこの PCH ファイルを使用するソース ファイルをコンパイルする必要があります、 **/Yu**<em>my_pch.h</em>オプション。 PCH ヘッダー ファイルは、PCH を使用するソース ファイルで最初に含める必要があります。

```cpp
// C2857.cpp
// Compile my_pch.cpp first, then
// compile by using: cl /EHsc /W4 /Yumy_pch.h my_project.cpp my_pch.obj
// Include the pch header before any other non-comment line
#include "my_pch.h"

int main()
{
    puts("Using a precompiled header file.\n");
}
```