---
title: インライン アセンブリの最適化
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: d4956ba12e0bc268d78a895e6cb1ec6e2059262a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166881"
---
# <a name="optimizing-inline-assembly"></a>インライン アセンブリの最適化

**Microsoft 固有の仕様**

有無、`__asm`関数内のブロックがいくつかの方法での最適化に影響します。 コンパイラはまず、最適化するために、`__asm`自体をブロックします。 アセンブリ言語で記述するものが正確に取得します。 2 番目の存在、`__asm`ブロックに影響は、変数の記憶域を登録します。 コンパイラで変数をレジスタ格納を回避できます、`__asm`ブロックでレジスタの内容に変更する場合、`__asm`ブロック。 最後に、いくつかその他の関数全体の最適化の場合は、アセンブリ言語で関数を含めることによって影響が受けるされます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[インライン アセンブラー](../../assembler/inline/inline-assembler.md)<br/>