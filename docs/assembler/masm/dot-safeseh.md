---
title: .SAFESEH
ms.date: 11/05/2019
f1_keywords:
- .SAFESEH
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
ms.openlocfilehash: 5953ad6bdf1d9d1b0070ce83dd1d764799b7440a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317566"
---
# <a name="safeseh-32-bit-masm"></a>.SAFESEH (32 ビット MASM)

関数を構造化例外ハンドラーとして登録します。 (32 ビット MASM のみ。)

## <a name="syntax"></a>構文

> **.SAFESEH** *識別子*

## <a name="remarks"></a>コメント

*識別子*は、ローカルに定義された[Proc](proc.md)または[extrn](extrn.md) proc の id である必要があります。 [ラベル](label-masm.md)は使用できません。 、.SAFESEH ディレクティブには、 [/safeseh](ml-and-ml64-command-line-reference.md) ml .exe コマンドラインオプションが必要です。

構造化例外ハンドラーの詳細については、「 [/safeseh](../../build/reference/safeseh-image-has-safe-exception-handlers.md)」を参照してください。

たとえば、安全な例外ハンドラーを登録するには、次のように新しい MASM ファイルを作成し、/safeseh でアセンブルして、リンクオブジェクトに追加します。

```asm
.386
.model  flat
MyHandler   proto
.safeseh    MyHandler
end
```

## <a name="see-also"></a>参照

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
