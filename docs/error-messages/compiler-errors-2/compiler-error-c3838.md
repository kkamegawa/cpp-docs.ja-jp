---
title: コンパイラ エラー C3838
ms.date: 11/04/2016
f1_keywords:
- C3838
helpviewer_keywords:
- C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
ms.openlocfilehash: 468fc5e8cb6b3a76880f12fe0aab14810f458a90
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741353"
---
# <a name="compiler-error-c3838"></a>コンパイラ エラー C3838

' type ' から明示的に継承することはできません

指定された `type` は、どのクラスの基底クラスとしても機能しません。

## <a name="example"></a>使用例

次の例では、C3838 が生成されます。

```cpp
// C3838a.cpp
// compile with: /clr /c
public ref class B : public System::Enum {};   // C3838
```
