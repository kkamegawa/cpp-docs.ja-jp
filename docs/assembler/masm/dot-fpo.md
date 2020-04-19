---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: ec08be4941f81abed55420884b34dc817caf3f13
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317735"
---
# <a name="fpo-32-bit-masm"></a>.FPO (32 ビット MASM)

**。FPO**ディレクティブは、デバッグレコードの出力を. debug $ F セグメントまたはセクションに制御します。 (32 ビット MASM のみ。)

## <a name="syntax"></a>構文

> **.FPO** (*cdwlocals*、 *cdwlocals*、 *cbprolog*、 *cbRegs*、 *fusebp*、 *cbprolog*)

### <a name="parameters"></a>パラメーター

*Cdwlocals*\
ローカル変数の数 (符号なし32ビット値)。

*Cdwparams*\
DWORD のパラメーターのサイズ (符号なし16ビット値)。

*Cbprolog*\
関数プロローグコード内のバイト数。符号なし8ビット値。

*cbRegs*\
Number レジスタが保存されました。

*Fusebp*\
EBP レジスタが割り当てられているかどうかを示します。 0または1のいずれかです。

*Cbframe*\
フレームの種類を示します。  詳細については、「 [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) 」を参照してください。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
