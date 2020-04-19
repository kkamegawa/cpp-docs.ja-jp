---
title: .ALLOCSTACK
ms.date: 12/17/2019
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: bcc94619dfa24ab5c8b5d23a60825641290ef176
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314186"
---
# <a name="allocstack"></a>.ALLOCSTACK

プロローグ内の現在のオフセットに対して、指定したサイズの**UWOP_ALLOC_SMALL**または**UWOP_ALLOC_LARGE**を生成します。

## <a name="syntax"></a>構文

> **.ALLOCSTACK** *サイズ*

## <a name="remarks"></a>コメント

MASM は、特定のサイズに対して最も効率的なエンコードを選択します。

**.ALLOCSTACK**を使用すると、ml64.exe ユーザーは、フレーム関数をアンワインドする方法を指定できます。プロローグ内では、 [PROC](proc.md) frame 宣言からに拡張され[ます。ENDPROLOG](dot-endprolog.md)ディレクティブ。 これらのディレクティブはコードを生成しません。`.xdata` と `.pdata`のみが生成されます。 **.ALLOCSTACK**の前には、アンワインドするアクションを実際に実装する命令が必要です。 アンワインドディレクティブと、マクロでアンワインドするコードをラップして、アグリーメントを保証することをお勧めします。

*サイズ*オペランドは8の倍数である必要があります。

詳細については、「 [MASM for x64 (ml64.exe)](masm-for-x64-ml64-exe.md)」を参照してください。

## <a name="sample"></a>［サンプル］

次の例は、アンワインド/例外ハンドラーを指定する方法を示しています。

```asm
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console
text SEGMENT
PUBLIC Example3
PUBLIC Example3_UW
Example3_UW PROC NEAR
   ; exception/unwind handler body

   ret 0

Example3_UW ENDP

Example3 PROC FRAME : Example3_UW

   sub rsp, 16
.allocstack 16

.endprolog

   ; function body
    add rsp, 16
   ret 0

Example3 ENDP
text ENDS
END
```

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
