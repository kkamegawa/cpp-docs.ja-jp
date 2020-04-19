---
title: コマンド ラインの警告 D9043
ms.date: 11/04/2016
f1_keywords:
- D9043
helpviewer_keywords:
- D9043
ms.assetid: 9263e28d-217b-414c-bfb6-86efd3c27a77
ms.openlocfilehash: 747f3cadd050b8f36c13fd28ae123f7a6dbdfb05
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992098"
---
# <a name="command-line-warning-d9043"></a>コマンド ラインの警告 D9043

' compiler_option ' の値 ' warning_level ' が無効です。' 4999 ' を想定しています。コード分析の警告は警告レベルに関連付けられていません

## <a name="example"></a>使用例

次の例では、C9043 が生成されます。

```cpp
// D9043.cpp
// compile with: /analyze /w16001
// D9043 warning expected
int main() {}
```
