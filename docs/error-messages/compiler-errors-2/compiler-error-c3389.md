---
title: コンパイラ エラー C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 6a9568f3c3be88438eae1f28e12dc780301ead0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402581"
---
# <a name="compiler-error-c3389"></a>コンパイラ エラー C3389

> _ _declspec (*キーワード*) では使用できません:/clr:pure または/clr:safe

## <a name="remarks"></a>Remarks

**/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

A [_ _declspec](../../cpp/declspec.md)修飾子の使用を意味するごとのプロセスの状態。  [/clr: 純粋な](../../build/reference/clr-common-language-runtime-compilation.md)意味、あたり[appdomain](../../cpp/appdomain.md)状態。  そのため、変数を宣言する、 `keyword` **_ _declspec**修飾子と指定してコンパイル **/clr: 純粋な**は許可されていません。

## <a name="example"></a>例

次の例では、C3389 が生成されます。

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```