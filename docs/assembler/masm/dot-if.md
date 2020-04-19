---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 6992ec8b151a83b3f9fa920997845c20caf0476d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317748"
---
# <a name="if-32-bit-masm"></a>.IF (32 ビット MASM)

*Condition1* (たとえば、AX > 7) をテストし、その条件が true の場合に*ステートメント*を実行するコードを生成します。 (32 ビット MASM のみ。)

## <a name="syntax"></a>構文

> **.** *Condition1*\
> *ステートメント*の\
> ⟦ **。ELSEIF** *condition2*\
> *ステートメント*⟧ \
> ⟦ **。それ以外**の\
> *ステートメント*⟧ \
> **.ENDIF**

## <a name="remarks"></a>コメント

の場合は[。それ以外](dot-else.md)の場合は、元の条件が false の場合にステートメントが実行されます。 条件は実行時に評価されることに注意してください。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
