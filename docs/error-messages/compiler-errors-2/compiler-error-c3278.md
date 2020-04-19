---
title: コンパイラ エラー C3278
ms.date: 11/04/2016
f1_keywords:
- C3278
helpviewer_keywords:
- C3278
ms.assetid: 56f818f5-85a6-4792-843b-54fe16327658
ms.openlocfilehash: 7618336c08dd111e495d7e4102b8e61c6e927c39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382089"
---
# <a name="compiler-error-c3278"></a>コンパイラ エラー C3278

> 直接インターフェイス メソッドまたはピュア メソッドの呼び出し '*メソッド*' は実行時に失敗

## <a name="remarks"></a>Remarks

インターフェイス メソッドまたはピュア メソッドが呼び出されましたが、このような呼び出しは許可されていません。

## <a name="example"></a>例

次の例では C3278 が生成されます。

```cpp
// C3278_2.cpp
// compile with: /clr
using namespace System;
interface class I
{
   void vmf();
};

public ref class C: public I
{
public:
   void vmf()
   {
      Console::WriteLine( "In C::vmf()" );
      I::vmf(); // C3278
   }

};

int main()
{
   C^ pC = gcnew C;
   pC->vmf();
}
```