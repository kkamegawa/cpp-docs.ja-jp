---
title: インライン アセンブリでのデータ ディレクティブと演算子
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: 52e20c37f3066122a062e3fc9c64ced576b6c302
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167232"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>インライン アセンブリでのデータ ディレクティブと演算子

**Microsoft 固有の仕様**

ただし、`__asm`ブロックは、C または C++ のデータ型とオブジェクトを参照できる、データ オブジェクトの MASM ディレクティブと演算子を定義できません。 具体的には、定義のディレクティブを使用することはできません**DB**、 `DW`、 **DD**、 `DQ`、 `DT`、および`DF`、または演算子`DUP`または**THIS** します。 MASM の構造とレコードもご利用いただけません。 インライン アセンブラーは、これらのディレクティブを受け入れません`STRUC`、 `RECORD`、**WIDTH**、または**MASK**します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__asm ブロックでのアセンブリ言語の使用](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
