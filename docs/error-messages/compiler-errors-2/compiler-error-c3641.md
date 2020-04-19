---
title: コンパイラ エラー C3641
ms.date: 11/04/2016
f1_keywords:
- C3641
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
ms.openlocfilehash: f6c27067e4f07c89b4226cf4d26adf2afb0b07ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385655"
---
# <a name="compiler-error-c3641"></a>コンパイラ エラー C3641

> '*関数*': 呼び出し/clr でコンパイルされた関数の場合、規則の 'calling_convention' が無効です:/clr:pure または/clr:safe

## <a name="remarks"></a>Remarks

**/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

のみ[_ _clrcall](../../cpp/clrcall.md)呼び出し規約は使用[/clr: 純粋な](../../build/reference/clr-common-language-runtime-compilation.md)します。

## <a name="example"></a>例

次の例では、C3641 が生成されます。

```cpp
// C3641.cpp
// compile with: /clr:pure /c
void __cdecl f() {}   // C3641
```