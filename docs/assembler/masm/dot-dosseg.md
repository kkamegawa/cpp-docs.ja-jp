---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: e27b0ae185542c11ee29119575d5c8225501f71e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313848"
---
# <a name="dosseg-32-bit-masm"></a>..DOSSEG (32 ビット MASM)

は、CODE first、DGROUP に含まれていないセグメント、および DGROUP 内のセグメントという MS-DOS セグメント規則に従ってセグメントを並べ替えます。 (32 ビット MASM のみ。)

## <a name="syntax"></a>構文

> **.DOSSEG**

## <a name="remarks"></a>コメント

DGROUP 内のセグメントは、BSS または STACK にないセグメント、BSS セグメント、および最後のスタックセグメントの順に続きます。 MASM のスタンドアロンプログラムでは、主に CodeView サポートを確保するために使用されます。 [.Dosseg](dosseg.md)と同じです。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
