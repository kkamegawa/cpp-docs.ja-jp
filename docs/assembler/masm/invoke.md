---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 7a005e5e70a2696ca89fb0ad1a3ff02aab8ffe5a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317189"
---
# <a name="invoke"></a>INVOKE

(32 ビット MASM のみ。)*式*によって指定されたアドレスでプロシージャを呼び出し、言語の種類の標準の呼び出し規約に従って、スタックまたはレジスタの引数を渡します。     

## <a name="syntax"></a>構文

> **呼び出し***式*⟦ __、__ *引数*...⟧

## <a name="remarks"></a>コメント

プロシージャに渡される各引数には、式、レジスタペア、またはアドレス式 ( **ADDR**で始まる式) を指定できます。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
