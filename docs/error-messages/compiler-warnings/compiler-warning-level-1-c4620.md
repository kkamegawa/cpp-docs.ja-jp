---
title: コンパイラの警告 (レベル 1) C4620
ms.date: 11/04/2016
f1_keywords:
- C4620
helpviewer_keywords:
- C4620
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
ms.openlocfilehash: d03c7d845923b918fbb665933147d8ff97cda7ab
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051461"
---
# <a name="compiler-warning-level-1-c4620"></a>コンパイラの警告 (レベル 1) C4620

型 'type' に対して後置形式の 'operator ++' は見つかりません。前置形式を使用します

指定した型の後置インクリメント演算子の定義がありません。 コンパイラは、オーバーロードされた前置演算子を使用します。

この警告は、後置 `++` 演算子を定義することで回避できます。 次に示すように、引数が 2 つのバージョンの `++` 演算子を作成します。

```cpp
// C4620.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator++()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator++(int)
   // {
   //    A tmp = *this;
   //    m_nData -= 1;
   //    return tmp;
   // }

private:
   int m_nData;
};

int main()
{
   A a(10);
   ++a;
   a++;   // C4620
}
```