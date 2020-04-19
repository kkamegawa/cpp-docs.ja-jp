---
title: コンパイラの警告 (レベル 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: ceb7e65a292e5b9e9ef960ca9553183b703c93f0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991687"
---
# <a name="compiler-warning-level-4-c4001"></a>コンパイラの警告 (レベル 4) C4001

非標準の拡張機能 ' 単一行コメント ' が使用されました

> [!NOTE]
> この警告は、単一行のコメントが C99 で標準であるため、Visual Studio 2017 バージョン15.5 では削除されます。

単一行コメントは、C99 以降C++の C では標準で標準です。
厳密な ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) では、単一行のコメントを含む C ファイルは、非標準の拡張機能の使用によって C4001 を生成します。 では単一行コメントが標準でC++あるため、1行のコメントを含む C ファイルは、Microsoft 拡張機能 (/ze) を使用してコンパイルするときに C4001 を生成しません。

## <a name="example"></a>使用例

警告を無効にするには #pragma 警告を非コメント化します[(disable: 4001)](../../preprocessor/warning.md)。

```cpp
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```
