---
title: コンパイラエラー C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: 6aff2e5c96e3c79fc748d8a95779d6a08647ab03
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739624"
---
# <a name="compiler-error-c2785"></a>コンパイラエラー C2785

' declaration1 ' と ' declaration2 ' の戻り値の型が異なります。

関数テンプレートの特殊化の戻り値の型が、プライマリ関数テンプレートの戻り値の型と異なります。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 関数テンプレートのすべての特殊化を一貫性のために確認します。

## <a name="example"></a>使用例

次の例では、C2785 が生成されます。

```cpp
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```
