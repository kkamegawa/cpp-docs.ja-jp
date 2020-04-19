---
title: コンパイラ エラー C2946
ms.date: 11/04/2016
f1_keywords:
- C2946
helpviewer_keywords:
- C2946
ms.assetid: c86dfbfc-7702-4f09-8a53-d205710e99c2
ms.openlocfilehash: c0ea10b3614e20e7f47c8f6632843544b4842751
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755370"
---
# <a name="compiler-error-c2946"></a>コンパイラ エラー C2946

明示的なインスタンス生成。'class' はテンプレート クラスの特殊化ではありません

非テンプレート クラスは明示的にインスタンス化できません。

## <a name="example"></a>使用例

次の例では C2946 が生成されます。

```cpp
// C2946.cpp
class C {};
template C;  // C2946
int main() {}
```
