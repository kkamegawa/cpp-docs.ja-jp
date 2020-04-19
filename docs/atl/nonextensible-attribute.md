---
title: nonextensible 属性
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: cc57acb8bd7bc3e32c764606da651f57316ceabf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250105"
---
# <a name="nonextensible-attribute"></a>nonextensible 属性

かどうかは、デュアル インターフェイスは実行時に拡張できません (つまり、メソッドまたはプロパティを使用してを提供しません`IDispatch::Invoke`は、vtable を使用して使用できません)、適用する必要があります、 **nonextensible**属性のインターフェイスを定義。 この属性は、コンパイル時に完全なコードの検証を有効にするために使用する (Visual Basic) などのクライアント言語に情報を提供します。 この属性が指定されていないバグが非表示のままクライアント コードで実行時まで。

詳細については、 **nonextensible**属性と例を参照してください[nonextensible](../windows/nonextensible.md)します。

## <a name="see-also"></a>関連項目

[デュアル インターフェイスと ATL](../atl/dual-interfaces-and-atl.md)
