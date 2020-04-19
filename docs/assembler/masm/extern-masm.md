---
title: EXTERN (MASM)
ms.date: 12/06/2019
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 681c4091a3c54a781bed4b01b235dfeb04f552c6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318099"
---
# <a name="extern"></a>EXTERN

型が*型*である、*名前*が1つ以上の外部変数、ラベル、またはシンボルを定義します。

## <a name="syntax"></a>構文

> **EXTERN** ⟦*language 型*⟧ *name* ⟦ __(__ *altid* __)__ ⟧ __:__ *type* ⟦ __,__ ⟦*language-type*⟧ *name* ⟦ __(__ *altid* __)__ ⟧ __:__ *type* ...⟧

## <a name="remarks"></a>コメント

*言語型*の引数は、32ビットの MASM でのみ有効です。

この*型*は[ABS](operator-abs.md)にすることができます。この場合、*名前*は定数としてインポートされます。 [Extrn](extrn.md)と同じです。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
