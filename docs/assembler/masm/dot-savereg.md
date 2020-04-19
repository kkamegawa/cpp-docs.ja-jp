---
title: .SAVEREG
ms.date: 12/16/2019
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: 18cb6e563084e8c5357bec2a8052a2b38fcdffee
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317553"
---
# <a name="savereg"></a>.SAVEREG

現在のプロローグオフセットを使用して、指定したレジスタ (*reg*) とオフセット (*オフセット*) の `UWOP_SAVE_NONVOL` または `UWOP_SAVE_NONVOL_FAR` アンワインドコードエントリを生成します。 MASM は、最も効率的なエンコードを選択します。

## <a name="syntax"></a>構文

> **.SAVEREG** *reg* __、__ *offset*

## <a name="remarks"></a>コメント

**.SAVEREG**を使用すると、ml64.exe ユーザーは、フレーム関数をアンワインドする方法を指定できます。プロローグ内では、 [PROC](proc.md) frame 宣言からに拡張され[ます。ENDPROLOG](dot-endprolog.md)ディレクティブ。 これらのディレクティブはコードを生成しません。`.xdata` と `.pdata`のみが生成されます。 **.SAVEREG**の前に、アンワインドするアクションを実際に実装する手順を指定する必要があります。 アンワインドディレクティブと、マクロでアンワインドするコードをラップして、アグリーメントを保証することをお勧めします。

詳細については、「 [MASM for x64 (ml64.exe)](masm-for-x64-ml64-exe.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
