---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 2cc5884a7473da9175a6b6af4b4251314deffeb4
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313393"
---
# <a name="externdef"></a>EXTERNDEF

型が*型*である、*名前*が1つ以上の外部変数、ラベル、またはシンボルを定義します。

## <a name="syntax"></a>構文

> **EXTERNDEF** ⟦*language-* type ⟧ *name* __:__ *type* ⟦ __,__ ⟦*language-* type ⟧ *name* __:__ *type* ...⟧

## <a name="remarks"></a>コメント

*言語型*の引数は、32ビットの MASM でのみ有効です。

*名前*がモジュールで定義されている場合は、[パブリック](public-masm.md)として扱われます。 *名前*がモジュールで参照されている場合は、 [EXTERN](extern-masm.md)として扱われます。 *名前*が参照されていない場合は無視されます。 この*型*は[ABS](operator-abs.md)にすることができます。この場合、*名前*は定数としてインポートされます。 通常はインクルードファイルで使用されます。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
