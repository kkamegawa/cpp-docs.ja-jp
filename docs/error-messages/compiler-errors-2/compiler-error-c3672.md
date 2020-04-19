---
title: コンパイラ エラー C3672
ms.date: 11/04/2016
f1_keywords:
- C3672
helpviewer_keywords:
- C3672
ms.assetid: da971041-1766-467a-aecf-1d8655c6cb7a
ms.openlocfilehash: 3288f7ea0b95d141dd6b4281d7080de1409da606
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758100"
---
# <a name="compiler-error-c3672"></a>コンパイラ エラー C3672

擬似デストラクター式は、関数呼び出しの一部としてのみ使用できます

デストラクターが正しく呼び出されませんでした。  詳細については、「[デストラクター](../../cpp/destructors-cpp.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3672 が生成されます。

```cpp
// C3672.cpp
template<typename T>
void f(T* pT) {
   &pT->T::~T;   // C3672
   pT->T::~T();   // OK
};

int main() {
   int i;
   f(&i);
}
```
