---
title: .PUSHREG
ms.date: 12/16/2019
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: de6ffd3668f47732144e8c632410f6dfde6b2f31
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318294"
---
# <a name="pushreg"></a>.PUSHREG

プロローグ内の現在のオフセットを使用して、指定したレジスタ番号に `UWOP_PUSH_NONVOL` アンワインドコードエントリを生成します。

## <a name="syntax"></a>構文

> .PUSHREG*レジスタ*

## <a name="remarks"></a>コメント

**.PUSHREG**を使用すると、ml64.exe ユーザーは、フレーム関数をアンワインドする方法を指定できます。これは、 [PROC](proc.md) **frame**宣言からに拡張されるプロローグ内でのみ使用でき[ます。ENDPROLOG](dot-endprolog.md)ディレクティブ。 これらのディレクティブはコードを生成しません。`.xdata` と `.pdata`のみが生成されます。 **.PUSHREG**の前には、アンワインドするアクションを実際に実装する手順が必要です。 アンワインドディレクティブと、マクロでアンワインドするコードをラップして、アグリーメントを保証することをお勧めします。

*register*は次のいずれかです: \
RAX |RCX |RDX |RBX |RDI |RSI |RBP |R8 |R9 |R10 |R11 |R12 |R13 |R14 |R15.

詳細については、「 [MASM for x64 (ml64.exe)](masm-for-x64-ml64-exe.md)」を参照してください。

## <a name="sample"></a>［サンプル］

### <a name="description"></a>説明

次の例は、非 volatile レジスタをプッシュする方法を示しています。

### <a name="code"></a>コード

```asm
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE
_text SEGMENT
Example1 PROC FRAME
   push r10
.pushreg r10
   push r15
.pushreg r15
   push rbx
.pushreg rbx
   push rsi
.pushreg rsi
.endprolog
   ; rest of function ...
   ret
Example1 ENDP
_text ENDS
END
```

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
