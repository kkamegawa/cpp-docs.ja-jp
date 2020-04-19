---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 0975e96e670400b7fa221ae2d1b9982b5cee613b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314147"
---
# <a name="code"></a>.CODE

(32 ビット MASM のみ。)と共に使用[します。モデル](dot-model.md)は、コードセグメントの開始を示します。

## <a name="syntax"></a>構文

> **.CODE** ⟦*name*⟧ \
> ⟦ *segmentItem* ⟧... \
> ⟦ *codesegmentnameId*の**終わり**;;⟧\

### <a name="parameters"></a>パラメーター

*名前*\
コードセグメントの名前を指定する省略可能なパラメーターです。 既定の名前は、小さい、小さい、コンパクト、およびフラット[モデル](dot-model.md)の場合に **_TEXT**ます。 既定の名前は、他のモデルの場合は*modulename*_TEXT です。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[.データ](dot-data.md)\
[MASM BNF 文法](masm-bnf-grammar.md)

