---
title: .SAVEXMM128
ms.date: 12/17/2019
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: 6402b75c10b1400d56923116621f00b4d0908822
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318255"
---
# <a name="savexmm128"></a>.SAVEXMM128

現在のプロローグオフセットを使用して、指定された XMM register および offset の `UWOP_SAVE_XMM128` または `UWOP_SAVE_XMM128_FAR` アンワインドコードエントリを生成します。 MASM は、最も効率的なエンコードを選択します。

## <a name="syntax"></a>構文

> **.SAVEXMM128** *xmmreg* 、 *offset*

## <a name="remarks"></a>コメント

**.SAVEXMM128**を使用すると、ml64.exe ユーザーは、フレーム関数をアンワインドする方法を指定できます。これは、 [PROC](proc.md) frame 宣言からに拡張されるプロローグ内でのみ使用でき[ます。ENDPROLOG](dot-endprolog.md)ディレクティブ。 これらのディレクティブはコードを生成しません。`.xdata` と `.pdata`のみが生成されます。 .SAVEXMM128 の前に、アンワインドするアクションを実際に実装する手順を指定する必要があります。 アンワインドディレクティブと、マクロでアンワインドするコードをラップして、アグリーメントを保証することをお勧めします。

*オフセット*は16の倍数である必要があります。

詳細については、「 [MASM for x64 (ml64.exe)](masm-for-x64-ml64-exe.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
