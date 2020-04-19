---
title: コンパイラ エラー C2141
ms.date: 11/04/2016
f1_keywords:
- C2141
helpviewer_keywords:
- C2141
ms.assetid: 10cf770f-0500-4220-ac90-a863b7ea5fe6
ms.openlocfilehash: 58b70eba6304dfe9d381ed0571c2497a852b9f3b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756514"
---
# <a name="compiler-error-c2141"></a>コンパイラ エラー C2141

配列サイズのオーバーフロー

配列が 2 GB の制限を超えています。 配列のサイズを小さくします。

## <a name="example"></a>使用例

次の例では、C2141 が生成されます。

```cpp
// C2141.cpp
// processor: IPF
class A {
   short m_n;
};

int main()
{
   A* pA = (A*)(-1);
   pA = new A[0x8000000000000001];   // C2141

   A* pA2 = (A*)(-1);
   pA2 = new A[0x80000000000000F];   // OK
}
```
