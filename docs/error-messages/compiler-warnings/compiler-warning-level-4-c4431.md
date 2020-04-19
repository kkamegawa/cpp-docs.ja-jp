---
title: コンパイラの警告 (レベル 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 102e9bdb2804988875d8c535eb8c266bd8fb03df
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683068"
---
# <a name="compiler-warning-level-4-c4431"></a>コンパイラの警告 (レベル 4) C4431

型指定子がありません - int と仮定しました。 メモ: C は、現在 int を既定値としてサポートしていません

このエラーは、Visual Studio 2005 で実行されたコンパイラ準拠作業の結果として生成C++される場合があります。既定では、型指定されていない識別子が int として作成されなくなりました。 識別子の型は明示的に指定する必要があります。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では、C4431 が生成されます。

```c
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```