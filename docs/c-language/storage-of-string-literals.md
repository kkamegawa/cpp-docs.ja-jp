---
title: 文字列リテラルの格納
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
ms.openlocfilehash: 0d505479f0844122826a2f07b57eaa69f33932e8
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148128"
---
# <a name="storage-of-string-literals"></a>文字列リテラルの格納

リテラル文字列の各文字は、連続するメモリ位置に順番に格納されます。 文字列リテラル内のエスケープ シーケンス (**\\\\** や **\\"** など) は、それぞれ 1 文字としてカウントされます。 (**\0** エスケープ シーケンスによって表される) null 文字は各文字列リテラルに自動的に追加され、その最後を示します (これは[変換フェーズ](../preprocessor/phases-of-translation.md) 7 で発生します)。2 つの同じ文字列が別々のアドレスに保存されない場合があることに注意してください。 [/GF](../build/reference/gf-eliminate-duplicate-strings.md) を指定すると、同じ文字列が複数ある場合に、その 1 つだけが実行可能ファイルに追加されます。

## <a name="remarks"></a>解説

**Microsoft 固有の仕様**

文字列には、静的ストレージ存続期間があります。 ストレージ存続期間については、「[ストレージ クラス](../c-language/c-storage-classes.md)」をご覧ください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[C 文字列リテラル](../c-language/c-string-literals.md)
