---
title: IF (MASM)
ms.date: 12/17/2019
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 38d366a3a41e7b08759594899cdcbb2cb84dfbfa
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317293"
---
# <a name="if"></a>IF

*Expression1*が true (0 以外) の場合は*ifstatements*のアセンブリを、 *expression1*が false (0)、 *expression2*が true の場合は*elseifstatements*を許可します。

## <a name="syntax"></a>構文

> *Expression1*\
> *if ステートメント*\
> ⟦**ELSEIF** *expression2*\
> *elseif-ステートメント*⟧ \
> ⟦**ELSE**\
> *else-ステートメント*⟧ \
> **ENDIF**

## <a name="remarks"></a>コメント

次のディレクティブは、 [ELSEIF](elseif-masm.md): **ELSEIFB**、 **ELSEIFDEF**、 **ELSEIFDIF**、 **ELSEIFDIFI**、 **ELSEIFE**、 **ELSEIFIDN**、ELSEIFIDNI、 **ELSEIFNB**、 **ELSEIFNDEF**の代わりに使用できます。 前の式が false の場合は、必要に応じて*else ステートメント*をアセンブルします。 式は、アセンブリ時に評価されることに注意してください。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
