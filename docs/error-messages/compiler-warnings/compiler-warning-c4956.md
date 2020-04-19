---
title: コンパイラの警告 C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: c15de8b22f56a2555cc763a45153139b1df01a31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280843"
---
# <a name="compiler-warning-c4956"></a>コンパイラの警告 C4956

> '*型*': この型は、検証できません

## <a name="remarks"></a>Remarks

この警告は、 [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) が指定され、コードに検証不可能な型が含まれている場合に生成されます。 **/Clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

詳細については、次を参照してください。[純粋で検証可能なコード (C +/cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)します。

この警告は、エラーとして表示されます。無効にするには、 [warning](../../preprocessor/warning.md) プラグマ、または [/wd](../../build/reference/compiler-option-warning-level.md) コンパイラ オプションを使用します。

## <a name="example"></a>例

次の例では C4956 が生成されます。

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```