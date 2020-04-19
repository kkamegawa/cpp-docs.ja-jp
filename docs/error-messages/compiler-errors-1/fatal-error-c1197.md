---
title: 致命的なエラー C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: 7f698262c73f0b311a92a8940107b552430919bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747242"
---
# <a name="fatal-error-c1197"></a>致命的なエラー C1197

プログラムが既に ' mscorlib. dll_2 ' を参照しているため、' mscorlib. dll_1 ' を参照できません

コンパイラは、共通言語ランタイムのバージョンと一致します。  ただし、以前のバージョンから共通言語ランタイムファイルのバージョンを参照しようとしました。

このエラーを解決するには、コンパイルしているビジュアルC++のバージョンに付属している共通言語ランタイムのバージョンからのファイルのみを参照します。

## <a name="example"></a>使用例

次の例では、C1197 が生成されます。

```cpp
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```
