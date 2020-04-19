---
title: CLongBinary クラス
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: 94666c0d15898e05ae78663a15d86b7d00d5c9c6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505674"
---
# <a name="clongbinary-class"></a>CLongBinary クラス

データベース上の大きなバイナリ データ オブジェクト (BLOB または "バイナリ ラージ オブジェクト" と呼びます) を使った作業を単純にします。

## <a name="syntax"></a>構文

```
class CLongBinary : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CLongBinary:: CLongBinary](#clongbinary)|`CLongBinary` オブジェクトを構築します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CLongBinary:: m_dwDataLength](#m_dwdatalength)|ハンドルがに`m_hData`格納されているデータオブジェクトの実際のサイズ (バイト単位) を格納します。|
|[CLongBinary:: m_hData](#m_hdata)|実際のイメージオブジェクトを表す Windows の HGLOBAL ハンドルを格納します。|

## <a name="remarks"></a>Remarks

たとえば、SQL テーブルのレコードフィールドには、画像を表すビットマップが含まれている場合があります。 オブジェクト`CLongBinary`は、そのようなオブジェクトを格納し、そのサイズを追跡します。

> [!NOTE]
>  一般に、 [DFX_Binary](record-field-exchange-functions.md#dfx_binary)関数と組み合わせて[CByteArray](../../mfc/reference/cbytearray-class.md)を使用することをお勧めします。 引き続きを使用`CLongBinary`することもできます`CByteArray`が、一般的に、Win32 ではより多くの機能が提供されます。これ`CByteArray`は、16ビットで発生したサイズの制限がなくなったためです。 このアドバイスは、データアクセスオブジェクト (DAO) と Open Database Connectivity (ODBC) を使用したプログラミングに適用されます。

`CLongBinary`オブジェクトを使用するには、レコードセットクラスで型`CLongBinary`のフィールドデータメンバーを宣言します。 このメンバーはレコードセットクラスの埋め込みメンバーになり、レコードセットの構築時に作成されます。 `CLongBinary`オブジェクトが構築されると、レコードフィールドエクスチェンジ (RFX) メカニズムによって、データソースの現在のレコードのフィールドからデータオブジェクトが読み込まれ、レコードが更新されるとレコードに保存されます。 RFX は、バイナリラージオブジェクトのサイズをデータソースに照会し、そのデータのストレージを ( `CLongBinary`オブジェクトの`m_hData`データメンバーを介して`HGLOBAL` ) 割り当て、データへのハンドル`m_hData`をに格納します。 また、RFX では、データオブジェクトの実際のサイズ`m_dwDataLength`もデータメンバーに格納されます。 `m_hData` Windows`HGLOBAL`ハンドルに格納されているデータの操作に通常使用するのと同じ手法を使用して、オブジェクト内のデータを使用して操作します。

レコードセットを破棄すると、埋め`CLongBinary`込みオブジェクトも破棄され、そのデストラクターが`HGLOBAL`データハンドルを解放します。

ラージオブジェクトとの`CLongBinary`使用の詳細については、「[レコードセット (ODBC)](../../data/odbc/recordset-odbc.md) 」 [および「レコードセット:大きなデータ項目の操作 (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdb_

##  <a name="clongbinary"></a>CLongBinary:: CLongBinary

`CLongBinary` オブジェクトを構築します。

```
CLongBinary();
```

##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength

の HGLOBAL ハンドル`m_hData`に格納されているデータの実際のサイズをバイト単位で格納します。

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Remarks

このサイズは、データに割り当てられたメモリブロックのサイズよりも小さくなる場合があります。 割り当てられたサイズを取得するには、Win32 [Globalsize](/windows/win32/api/winbase/nf-winbase-globalsize)関数を呼び出します。

##  <a name="m_hdata"></a>  CLongBinary::m_hData

Windows の HGLOBAL ハンドルを実際のバイナリラージオブジェクトデータに格納します。

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)
