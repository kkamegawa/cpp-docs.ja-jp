---
title: .STACK
ms.date: 11/05/2019
f1_keywords:
- .STACK
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
ms.openlocfilehash: 4dd45a0705b729e65bb413fc02671f86e5f9105b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318229"
---
# <a name="stack-32-bit-masm"></a>.スタック (32 ビット MASM)

と共に使用[します。モデル](dot-model.md)は、(セグメント名**スタック**を持つ) スタックセグメントを定義します。 オプションの*サイズ*は、スタックのバイト数を指定します (既定値は 1024)。 **。Stack ディレクティブは**、stack ステートメントを自動的に閉じます。 (32 ビット MASM のみ。)

## <a name="syntax"></a>構文

> **.STACK** ⟦*size*⟧

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
