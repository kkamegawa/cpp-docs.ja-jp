---
title: コンパイラの警告 (レベル 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 43570cd43ca6e9d4f892dc577f615e9fa980e561
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051576"
---
# <a name="compiler-warning-level-3-c4414"></a>コンパイラの警告 (レベル 3) C4414

' function ': near に変換された関数への short ジャンプ

短いジャンプは、命令から制限された範囲内のアドレスに分岐するコンパクト命令を生成します。 命令には、ジャンプとターゲットアドレス (関数定義) との距離を表す短いオフセットが含まれます。 リンク中に、関数が移動されるか、またはリンク時の最適化の対象になります。これにより、関数が短いオフセットから到達可能な範囲外に移動されます。 コンパイラは、ジャンプ用に特別なレコードを生成する必要があります。そのためには、jmp 命令を NEAR 以上にする必要があります。 コンパイラによって変換が行われました。

たとえば、次のコードでは C4414 が生成されます。

```cpp
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```