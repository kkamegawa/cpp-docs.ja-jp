---
title: コンパイラエラー C2005
ms.date: 11/04/2016
f1_keywords:
- C2005
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
ms.openlocfilehash: ff998beaa1d954f05a07d8ccf1b59cec0f4e3958
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737479"
---
# <a name="compiler-error-c2005"></a>コンパイラエラー C2005

\#行には行番号が必要ですが、' token ' が見つかりました。

`#line` ディレクティブの後には、行番号を指定する必要があります。

次の例では、C2005 が生成されます。

```cpp
// C2005.cpp
int main() {
   int i = 0;
   #line i   // C2005
}
```

解決方法:

```cpp
// C2005b.cpp
int main() {
   int i = 0;
   #line 0
}
```
