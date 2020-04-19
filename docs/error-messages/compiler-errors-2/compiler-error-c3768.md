---
title: コンパイラ エラー C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: e9c385fd178dc967e72f5e0ca7fab27b28ad962f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400215"
---
# <a name="compiler-error-c3768"></a>コンパイラ エラー C3768

> 純粋なマネージ コードで仮想 vararg 関数のアドレスを取得できません。

## <a name="remarks"></a>Remarks

**/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

コンパイルするときに **/clr: 純粋な**、仮想のアドレスを取得できません`vararg`関数。

## <a name="example"></a>例

次の例では、C3768 が生成されます。

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```