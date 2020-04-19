---
title: Wide Characters (ワイド文字)
ms.date: 11/04/2016
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
ms.openlocfilehash: 868acf0abd26a1f4b5533bb997fb9ea09a27954b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151963"
---
# <a name="wide-characters"></a>Wide Characters (ワイド文字)

**ANSI 3.1.3.4** 複数の文字を含む整数文字定数、または、複数のマルチバイト文字を含むワイド文字定数の値

通常の文字定数 'ab' は、整数値 (int)0x6162 を持ちます。 1 バイトを超える場合は、以前に読み取られたバイトが **CHAR_BIT** の値だけ左にシフトされ、次のバイトがビットごとの OR 演算子を使用して **CHAR_BIT** 分の下位ビットと比較されます。 マルチバイト文字定数のバイト数は sizeof (int) を超えることはできません。これは 32 ビット対象のコードでは 4 です。

マルチバイト文字定数は、上記のように読み取られ、これが `mbtowc` ランタイム関数を使用してワイド文字定数に変換されます。 結果が有効なワイド文字定数でない場合は、エラーが発行されます。 いずれの場合も、`mbtowc` 関数でチェックするバイト数は `MB_CUR_MAX` の値に制限されます。

## <a name="see-also"></a>関連項目

[文字](../c-language/characters.md)
