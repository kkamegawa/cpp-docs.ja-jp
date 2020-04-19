---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 23c6b0aefae856da449da574669e8475122c7556
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312951"
---
# <a name="macro"></a>MACRO

マクロブロックを*名前*としてマークし、マクロが呼び出されたときに渡される引数の*パラメーター*のプレースホルダーを確立します。

## <a name="syntax"></a>構文

> *name***マクロ**⟦*parameter* ⟦ **: REQ** |: =*既定* | *args* **: VARARG**⟧...⟧\
> *ステートメント*の\
⟦**GOTO** :*マクロ lab d*⟧ \
> ⟦**Exitm**⟧ \
> **Endm** ⟦*value*⟧

## <a name="remarks"></a>コメント

マクロ関数は、呼び出し元のステートメントに*値*を返します。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[GOTO (MASM)](goto-masm.md)\
[Endm](endm.md)\
[MASM BNF 文法](masm-bnf-grammar.md)

