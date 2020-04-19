---
title: コンパイラ エラー C3247
ms.date: 11/04/2016
f1_keywords:
- C3247
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
ms.openlocfilehash: 81dc5d5e54551aff49adad2ada2eb25f57a37ec2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754382"
---
# <a name="compiler-error-c3247"></a>コンパイラ エラー C3247

'class1': コクラスは他のコクラス 'class2' から継承できません

[coclass](../../windows/coclass.md) 属性でマークされたクラスは `coclass` 属性でマークされた別のクラスから継承できません。

次の例では C3247 が生成されます。

```cpp
// C3247.cpp
[module(name="MyLib")];
[coclass]
class a {
};

[coclass]
class b : public a {   // C3247
};
int main() {
}
```
