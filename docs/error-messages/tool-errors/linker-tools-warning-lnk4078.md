---
title: リンカー ツールの警告 LNK4078
ms.date: 11/04/2016
f1_keywords:
- LNK4078
helpviewer_keywords:
- LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
ms.openlocfilehash: 9ce72f476aa85434acd5277d0307ffc61e0a0214
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990991"
---
# <a name="linker-tools-warning-lnk4078"></a>リンカー ツールの警告 LNK4078

異なる属性を持つ複数の ' section name ' セクションが見つかりました

リンクが、同じ名前で属性が異なる2つ以上のセクションが見つかりました。

この警告は、以前のバージョンのリンクまたは LIB によって作成されたインポートライブラリまたはエクスポートファイルが原因で発生する場合があります。

ファイルを再作成して再リンクします。

## <a name="example"></a>使用例

LNK4078 は、互換性に影響する変更によって発生することもあります。 x86 上の[init_seg](../../preprocessor/init-seg.md)によって名前が付けられたセクションは読み取り/書き込みであり、現在は読み取り専用です。

次の例では、LNK4078 が生成されます。

```cpp
// LNK4078.cpp
// compile with: /W1
// LNK4078 expected
#include <stdio.h>
#pragma warning(disable : 4075)
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // pointers to destructors.

struct A { A() {} };

int myexit (PF pf) { return 0; }

#pragma section(".mine$a", read, write)
// try the following line instead
// #pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) int ii = 1;

#pragma section(".mine$z", read, write)
// try the following line instead
// #pragma section(".mine$z", read)
__declspec(allocate(".mine$z")) int i = 1;

#pragma data_seg()
#pragma init_seg(".mine$m", myexit)
A bbbb;
A cccc;
int main() {}
```
