---
title: GOTO (MASM)
ms.date: 12/16/2019
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: f198658f9a4b85e0b5ec9b7a0c122241e57286f6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317280"
---
# <a name="goto"></a>GOTO

アセンブリを、"_マクロラベル_"**とマークさ**れた行に転送します。

## <a name="syntax"></a>構文

> **GOTO** *マクロラベル*

## <a name="remarks"></a>コメント

**GOTO** [は、](for-masm.md)[マクロ](macro.md)内、 [forc](forc.md)、 [REPEAT](repeat.md)、および[WHILE](while-masm.md)ブロックでのみ許可されます。 *マクロラベル*のターゲットは、行の唯一のディレクティブである必要があります。先頭にはコロンを付ける必要があります。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
