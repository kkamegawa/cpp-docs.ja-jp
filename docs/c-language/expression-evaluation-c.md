---
title: 式の評価 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
ms.openlocfilehash: 37affedc0bcf3fb1423898ecf2c570794d9625c0
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151092"
---
# <a name="expression-evaluation-c"></a>式の評価 (C)

代入、単項インクリメント、単項デクリメント、または関数呼び出しが含まれている式は、式の評価に付随する結果 (副作用) が生じる場合があります。 "シーケンス ポイント" に達すると、すべての副作用を含む、シーケンス ポイントより前にあるすべてのものが、シーケンス ポイントより後のものの評価が開始される前に、評価されることが保証されます。

"副作用" は式の評価による変更です。 副作用は、式の評価によって変数の値が変更されるたびに発生します。 すべての代入演算子に副作用があるわけではありません。 関数呼び出しでは、直接割り当てまたはポインター経由での間接割り当てにより外部から参照できる項目の値を変更すると、副作用が生じることもあります。

## <a name="see-also"></a>関連項目

[オペランドおよび式](../c-language/operands-and-expressions.md)
