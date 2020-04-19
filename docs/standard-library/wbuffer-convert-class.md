---
title: wbuffer_convert クラス
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: 8de0091af93120290105ce7603fae5acff257b76
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688539"
---
# <a name="wbuffer_convert-class"></a>wbuffer_convert クラス

バイト ストリーム バッファーとの間の要素の転送を制御するストリーム バッファーを説明します。

## <a name="syntax"></a>構文

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Codecvt*|変換オブジェクトを表す[ロケール](../standard-library/locale-class.md) ファセット。|
|*Elem*|ワイド文字要素型。|
|*Traits*|*Elem* と関連付けられている特徴。|

## <a name="remarks"></a>Remarks

このクラステンプレートは、`_Elem` 型の要素の転送を制御するストリームバッファーを記述します。このストリームバッファーは、文字の特徴がクラス `Traits` によって記述されており、`std::streambuf` 型のバイトストリームバッファーとの間で伝送されます。

`Elem` 値のシーケンスとマルチバイト シーケンスとの間の変換は、クラス `Codecvt<Elem, char, std::mbstate_t>` のオブジェクトによって実行されます。このことは、標準コード変換ファセット `std::codecvt<Elem, char, std::mbstate_t>` の要件を満たしています。

このクラステンプレートのオブジェクトは、次のものを格納します。

- 基になるバイト ストリーム バッファーへのポインター

- 割り当てられた変換オブジェクトへのポインター ([wbuffer_convert](../standard-library/wbuffer-convert-class.md) のときに解放される)
