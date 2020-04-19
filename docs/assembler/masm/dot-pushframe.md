---
title: .PUSHFRAME
description: について説明します。PUSHFRAME MASM ディレクティブ。フレーム関数をアンワインドする方法を指定するために使用されます。
ms.date: 12/06/2019
f1_keywords:
- .PUSHFRAME
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
ms.openlocfilehash: 0aaec119d26d87fddb1eba505458da1250a5926e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317579"
---
# <a name="pushframe"></a>.PUSHFRAME

アンワインドコードエントリ `UWOP_PUSH_MACHFRAME` を生成します。 省略可能な**code**キーワードが指定されている場合、アンワインドコードのエントリには1という修飾子が与えられます。 それ以外の場合、修飾子は0です。

## <a name="syntax"></a>構文

> **.PUSHFRAME** ⟦**CODE**⟧;;

## <a name="remarks"></a>コメント

.PUSHFRAME を使用すると、ml64.exe ユーザーは、フレーム関数をアンワインドする方法を指定できます。 これはプロローグ内でのみ許可されます。これは、 [PROC](proc.md) FRAME 宣言からにまで拡張され[ます。ENDPROLOG](dot-endprolog.md)ディレクティブ。 これらのディレクティブはコードを生成しません。`.xdata` と `.pdata`のみが生成されます。 **.PUSHFRAME**の前には、アンワインドするアクションを実際に実装する命令が必要です。 アグリーメントを保証するために、アンワインドディレクティブとマクロでアンワインドするコードの両方をラップすることをお勧めします。

詳細については、「 [MASM for x64 (ml64.exe)](masm-for-x64-ml64-exe.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
