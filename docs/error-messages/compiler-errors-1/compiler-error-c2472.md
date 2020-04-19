---
title: コンパイラ エラー C2472
ms.date: 11/04/2016
f1_keywords:
- C2472
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
ms.openlocfilehash: d2f104bb61915f8d19d5fff22eea17929c0e8d74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350911"
---
# <a name="compiler-error-c2472"></a>コンパイラ エラー C2472

> '*関数*' マネージ コードで生成することはできません: '*メッセージ*' です混合イメージを生成する/clr と共にコンパイル。

## <a name="remarks"></a>Remarks

このエラーは、純粋な共通言語ランタイム (CLR) の環境内で、マネージド コードでサポートされていない型を使用すると発生します。 エラーを解決するには、 **/clr** を使用してコンパイルします。

**/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

## <a name="example"></a>例

次の例では警告 C2472 が生成されます。

```cpp
// C2472.cpp
// compile with: /clr:pure
// C2472 expected

#include <cstdlib>

int main()
{
   int * __ptr32 p32;
   int * __ptr64 p64;

   p32 = (int * __ptr32)malloc(4);
   p64 = p32;
}
```

## <a name="see-also"></a>関連項目

- [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)
