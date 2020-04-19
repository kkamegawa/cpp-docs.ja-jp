---
title: コンパイラ エラー C2825
ms.date: 11/04/2016
f1_keywords:
- C2825
helpviewer_keywords:
- C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
ms.openlocfilehash: 6a51901477958056356a96d71adde4241d60a2ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750586"
---
# <a name="compiler-error-c2825"></a>コンパイラ エラー C2825

var: ':: ' が後に続く場合は、クラスまたは名前空間でなければなりません

修飾名を作成しようとしましたが、失敗しました。

たとえば、関数名が:: で始まる関数宣言がコードに含まれていないことを確認します。

## <a name="example"></a>使用例

次の例では、C2825 が生成されます。

```cpp
// C2825.cpp
typedef int i;
int main() {
   int* p = new int;
   p->i::i();   // C2825
   // try the following line instead
   // p->i::~i();
}
```
