---
title: OPTION (MASM)
ms.date: 12/17/2019
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: bd50ac2e051db7f02ac077054e5856524745df54
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318749"
---
# <a name="option"></a>OPTION

アセンブラーの機能を有効または無効にします。

## <a name="syntax"></a>構文

> **オプションオプション**の*一覧*

## <a name="remarks"></a>コメント

使用可能なオプションには次のものがあります。

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**エミュレーター**|
|**NOEMULATOR**|**EPILOGUE**|**EXPR16**|**EXPR32**|
|**LANGUAGE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**OFFSET**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**プロローグ**|**READONLY**|**NOREADONLY**|
|**役割**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|

言語の構文は、 **OPTION language:** <em>x</em>です。ここで、 *x*は C、SYSCALL、STDCALL、PASCAL、FORTRAN、または BASIC.  SYSCALL、PASCAL、FORTRAN、および BASIC は、ではサポートされていません[。モデル](dot-model.md)フラット。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
