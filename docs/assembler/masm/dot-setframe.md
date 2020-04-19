---
title: .SETFRAME
ms.date: 12/17/2019
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: 8c491a811634995398a37aa001cc1c93f8434114
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318242"
---
# <a name="setframe"></a>.SETFRAME

指定されたレジスタ (*reg*) とオフセット (*オフセット*) を使用して、アンワインド情報のフレームレジスタフィールドおよびオフセットを設定します。 オフセットは、16の倍数で240以下である必要があります。 また、このディレクティブは、現在のプロローグオフセットを使用して、指定されたレジスタの `UWOP_SET_FPREG` アンワインドコードエントリを生成します。

## <a name="syntax"></a>構文

> **.SETFRAME** *reg*、 *offset*

## <a name="remarks"></a>コメント

**.SETFRAME**を使用すると、ml64.exe ユーザーは、フレーム関数をアンワインドする方法を指定できます。これは、 [PROC](proc.md) frame 宣言からに拡張されたプロローグ内でのみ使用でき[ます。ENDPROLOG](dot-endprolog.md)ディレクティブ。 これらのディレクティブはコードを生成しません。`.xdata` と `.pdata`のみが生成されます。 **.SETFRAME**の前には、アンワインドするアクションを実際に実装する命令が必要です。 アンワインドディレクティブと、マクロでアンワインドするコードをラップして、アグリーメントを保証することをお勧めします。

詳細については、「 [MASM for x64 (ml64.exe)](masm-for-x64-ml64-exe.md)」を参照してください。

## <a name="sample"></a>［サンプル］

### <a name="description"></a>説明

次のサンプルは、フレームポインターの使用方法を示しています。

### <a name="code"></a>コード

```asm
; ml64 frmex2.asm /link /entry:frmex2 /SUBSYSTEM:CONSOLE
_text SEGMENT
frmex2 PROC FRAME
   push rbp
.pushreg rbp
   sub rsp, 010h
.allocstack 010h
   mov rbp, rsp
.setframe rbp, 0
.endprolog
   ; modify the stack pointer outside of the prologue (similar to alloca)
   sub rsp, 060h

   ; we can unwind from the following AV because of the frame pointer
   mov rax, 0
   mov rax, [rax] ; AV!

   add rsp, 060h
   add rsp, 010h
   pop rbp
   ret
frmex2 ENDP
_text ENDS
END
```

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
