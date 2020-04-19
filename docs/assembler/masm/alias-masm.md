---
title: ALIAS (MASM)
ms.date: 12/17/2019
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 5aef169c5632e74722438c63718ce5b783a8da09
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316604"
---
# <a name="alias"></a>ALIAS

**ALIAS**ディレクティブは、関数の代替名を作成します。  これにより、関数に対して複数の名前を作成したり、リンカー (convert.exe) が古い関数を新しい関数にマップできるようにするライブラリを作成したりできます。

## <a name="syntax"></a>構文

> **エイリアス \<** _エイリアス_ **> = \<** _実際の名前_ **>**

#### <a name="parameters"></a>パラメーター

*実際の名前*\
関数またはプロシージャの実際の名前。  山かっこが必要です。

*エイリアス*\
代替名または別名。  山かっこが必要です。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
