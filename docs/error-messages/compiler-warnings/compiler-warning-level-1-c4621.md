---
title: コンパイラの警告 (レベル 1) C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: 9dd4defe18a94f65e265d02f6c26c715667cd696
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052600"
---
# <a name="compiler-warning-level-1-c4621"></a>コンパイラの警告 (レベル 1) C4621

型 ' type ' に対して後置形式でない ' operator--' が見つかりました。プレフィックス形式を使用します

指定された型に後置デクリメント演算子が定義されていませんでした。 コンパイラは、オーバーロードされた前置演算子を使用します。

この警告は、後置 `--` 演算子を定義することで回避できます。 次に示すように、`--` 演算子の2つの引数を持つバージョンを作成します。

```cpp
// C4621.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator--()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator--(int)
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
   --a;
   a--;   // C4621
}
```