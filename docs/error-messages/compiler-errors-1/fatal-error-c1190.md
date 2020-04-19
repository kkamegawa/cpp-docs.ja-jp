---
title: 致命的なエラー C1190
ms.date: 11/04/2016
f1_keywords:
- C1190
helpviewer_keywords:
- C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
ms.openlocfilehash: 261d25d031d3a11f1d9e25ca3fb2c926cd521f97
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747346"
---
# <a name="fatal-error-c1190"></a>致命的なエラー C1190

マネージド ターゲット コードには '/clr' が必要です。

CLR コンストラクトを使用していますが、 **/clr**を指定していませんでした。

詳細については、「[/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)」を参照してください。

次の例では C1190 が生成されます。

```cpp
// C1190.cpp
// compile with: /c
__gc class A {};   // C1190
ref class A {};
```
