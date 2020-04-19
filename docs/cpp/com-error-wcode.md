---
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: f33871634b516723c94fead847f64ef20d25513f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399318"
---
# <a name="comerrorwcode"></a>_com_error::WCode

**Microsoft 固有の仕様**

カプセル化された HRESULT にマップされた 16 ビット エラー コードを取得します。

## <a name="syntax"></a>構文

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>戻り値

HRESULT が範囲 0x80040200 を 0x8004FFFF 内にある場合、`WCode`から 0x80040200 を引いた HRESULT を返します。 それ以外の場合、0 を返します。

## <a name="remarks"></a>Remarks

`WCode`メソッドを使用して、COM サポート コード内で発生したマッピングを元に戻します。 ラッパーは、`dispinterface`プロパティまたはメソッド呼び出しの引数と呼び出しにパッケージ化するサポート ルーチン`IDispatch::Invoke`します。 関数が戻るとき場合のエラー HRESULT の`DISP_E_EXCEPTION`からエラー情報を取得、返される、`EXCEPINFO`に構造体が渡される`IDispatch::Invoke`します。 エラー コードはいずれかに格納されている 16 ビット値、`wCode`のメンバー、`EXCEPINFO`構造体またはで完全な 32 ビット値、`scode`のメンバー、`EXCEPINFO`構造体。 場合、16 ビット`wCode`返されるか、32 ビットのエラー HRESULT を最初にマップする必要があります。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error クラス](../cpp/com-error-class.md)