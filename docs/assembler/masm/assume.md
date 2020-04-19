---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: a74a5336e626f561f1fc61e866792ce193332d84
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316539"
---
# <a name="assume"></a>ASSUME

レジスタ値のエラーチェックを有効にします。 (32 ビット MASM のみ。)

## <a name="syntax"></a>構文

> *Segregister* __:__ *name* ⟦ __,__ *segregister* __:__ *name*...⟧\
> 次のように*dataregister* __:__ *type* ⟦ __,__ *dataregister* __:__ *type*...⟧\
> *レジスタ* __: error__ ⟦ __、__ *register* __: error__...⟧\
> **⟦** *Register* __:__ ⟧**NOTHING** ⟦ __、__ *register* __: nothing__...⟧

## <a name="remarks"></a>コメント

が有効になる**と**、アセンブラーは、指定されたレジスタの値に対する変更を監視します。 レジスタが使用されている場合、**ERROR**によってエラーが生成されます。 レジスタエラーチェックは何も削除され**NOTHING**。 1つのステートメントでさまざまな種類の仮定を組み合わせることができます。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
