---
title: codecvt_utf8_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::cvt_utf8_utf16
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
ms.openlocfilehash: 879ebe6a75d76a84ef4250b95c41e02eccba5517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458646"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

UTF-16 としてエンコードされたワイド文字と、UTF-8 としてエンコードされたバイト ストリームを変換する[ロケール](../standard-library/locale-class.md) ファセットを表します。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>パラメーター

*Elem*\
ワイド文字要素型。

*Maxcode*\
ロケール ファセットの文字の最大数。

*Mode*\
ロケール ファセットの構成情報。

## <a name="remarks"></a>Remarks

このバイト ストリームはバイナリ ファイルまたはテキスト ファイルに書き込むことができます。

## <a name="requirements"></a>必要条件

ヘッダー: \<codecvt >

名前空間: std
