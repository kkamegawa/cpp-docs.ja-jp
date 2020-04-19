---
title: PROC
ms.date: 12/06/2019
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: 85d9a1e82eebcd83cb0f12f5ca751ec9415af18d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318671"
---
# <a name="proc"></a>PROC

*Label*と呼ばれるプロシージャブロックの開始と終了をマークします。 ブロック内のステートメントは、 **CALL**命令または[INVOKE](invoke.md)ディレクティブを使用して呼び出すことができます。

## <a name="syntax"></a>構文

> *label* **PROC** ⟦*distance*⟧⟦*language-type*⟧⟦ **PUBLIC** | **PRIVATE** | **EXPORT** ⟧⟦ __\<__ *prologu氏 g* __>__ ⟧⟦**は** *reglist*⟧⟦ __、__ *parameter* ⟦ __:__ *tag*⟧...⟧\
> ⟦**FRAME** ⟦ __:__ *ehandler-address*⟧⟧ \
> *ステートメント*の\
> *ラベル*の**endp**

## <a name="remarks"></a>コメント

⟦*Distance*⟧と⟦*language type*⟧引数は、32ビット MASM でのみ有効です。

⟦**FRAME** ⟦ __:__ *ehandler-address*⟧⟧は ml64.exe でのみ有効であり、MASM は .xdata 内の関数テーブルエントリを生成し、関数の構造化例外処理のアンワインド動作を実行します。

**FRAME**属性を使用する場合は、の後にを指定する必要があり[ます。ENDPROLOG](dot-endprolog.md)ディレクティブ。

Ml64.exe の使用方法の詳細については、「 [MASM for x64 (ml64.exe)](masm-for-x64-ml64-exe.md) 」を参照してください。

## <a name="example"></a>使用例

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

上記のコードでは、次の関数テーブルとアンワインド情報が出力されます。

```Output
FileHeader->Machine 34404
Dumping Unwind Information for file ex2.exe

.pdata entry 1 0x00001000 0x00001023

  Unwind data: 0x00002000

    Unwind version: 1
    Unwind Flags: None
    Size of prologue: 0x08
    Count of codes: 3
    Frame register: rbp
    Frame offset: 0x0
    Unwind codes:

      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00
      Code offset: 0x05, ALLOC_SMALL, size=0x10
      Code offset: 0x01, PUSH_NONVOL, register=rbp
```

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
