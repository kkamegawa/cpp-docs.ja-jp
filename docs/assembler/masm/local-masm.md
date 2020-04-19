---
title: LOCAL (MASM)
ms.date: 12/16/2019
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 2bef6b26f1b922be6512bd6ebe8e0b2627e86f45
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317150"
---
# <a name="local"></a>LOCAL

最初のディレクティブでは、マクロ内で、マクロの各インスタンスに固有のラベル**を定義し**ます。

## <a name="syntax"></a>構文

> **LOCAL** *LocalId* ⟦、 *localId* ...⟧
>
> **ローカル** *lab⟦ d* __\[__ *count* __]__ ⟧⟦ __:__ *qualifiedType*⟧⟦ __,__ *lab d* ⟦ __\[__ *count* __]__ ⟧⟦*qualifiedType*⟧...⟧

## <a name="remarks"></a>コメント

2番目のディレクティブでは、プロシージャ定義 (**PROC**) 内で、プロシージャの実行中に存在するスタックベースの変数を**ローカル**で作成します。 *Labに*は、単純な変数または*count*要素を含む配列を指定できます。 *count*は定数式です。

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
