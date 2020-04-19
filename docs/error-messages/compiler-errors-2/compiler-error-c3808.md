---
title: コンパイラ エラー C3808
ms.date: 11/04/2016
f1_keywords:
- C3808
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
ms.openlocfilehash: 0a1b0b82241c6e48d2c1941ff8122697d11492eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352989"
---
# <a name="compiler-error-c3808"></a>コンパイラ エラー C3808

> '*型*': ComImport 属性を持つクラス メンバーを定義できません'*メンバー*'、のみを抽象化または dllimport 関数が許可されています。

## <a name="remarks"></a>Remarks

派生した型<xref:System.Runtime.InteropServices.ComImportAttribute>は定義できません*メンバー*します。

**/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

## <a name="example"></a>例

次の例では、C3808 が生成されます。

```cpp
// C3808.cpp
// compile with: /c /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 {
   int f() {}   // C3808
   virtual int g() abstract;   // OK

   [DllImport("msvcrt.dll")]
   int printf(System::String ^, int i);   // OK
};
```