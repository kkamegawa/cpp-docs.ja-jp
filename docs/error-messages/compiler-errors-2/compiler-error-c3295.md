---
title: コンパイラ エラー C3295
ms.date: 11/04/2016
f1_keywords:
- C3295
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
ms.openlocfilehash: 4ee79e87085b0b939a762fec4c576c393846c2ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756865"
---
# <a name="compiler-error-c3295"></a>コンパイラ エラー C3295

'#pragma pragma' は、グローバルまたは名前空間スコープでのみ使用できます

一部のプラグマは関数内では使用できません。  詳細について[は、「プラグマディレクティブ」と「__Pragma キーワード](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C3295 が生成されます。

```cpp
// C3295.cpp
int main() {
   #pragma managed   // C3295
}
```
