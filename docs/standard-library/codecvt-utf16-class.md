---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: a84ca6da22825ca3fa7ab43e43a574fb05caa1a8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689825"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

UCS-2 または UCS-4 としてエンコードされたワイド文字と、UTF-16LE または UTF-16BE としてエンコードされたバイト ストリームを変換する[ロケール](../standard-library/locale-class.md) ファセットを表します。

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>パラメーター

*Elem* \
ワイド文字要素型。

*Maxcode* \
ロケール ファセットの文字の最大数。

*モード*\
ロケール ファセットの構成情報。

## <a name="remarks"></a>Remarks

このクラステンプレートは、UCS 2 または UCS 4 としてエンコードされたワイド文字と、16LE としてエンコードされたバイトストリームを変換します (モード & little_endian の場合)。それ以外の場合は UTF-16 を使用します。

このバイト ストリームはバイナリ ファイルに書き込む必要があります。テキスト ファイルに書き込むと、破損する場合があります。

## <a name="requirements"></a>［要件］

ヘッダー: \<codecvt >

名前空間: std